---
tags: [animation, graphics, gltf]
aliases: [Skinning, 蒙皮]
---

# Skinning (蒙皮)

本文详细介绍了 glTF 规范中的蒙皮（Skinning）机制，包括核心概念辨析、数据结构关系以及底层的数学逻辑。

---

## 1. glTF 核心概念

### 如何判断一个 Node 是否是 Joint
在 glTF 规范中，Node 本身并没有 `isJoint` 标志。判断标准如下：
1. **被 Skin 引用**：查看 `skins[].joints` 数组。如果 Node 索引在其中，它就是 Joint。
2. **层次结构**：Joint 通常作为骨骼层次结构的一部分存在。
3. **Skin 关联**：一个 Node 可以通过其 `skin` 属性关联到一个 skin 对象，表示该 Node 的 Mesh 受到该 skin 驱动。

> **总结**：要确认 Node $i$ 是否是 Joint，需遍历所有 `skins[].joints`。

### 架构纠偏：`joints` 数组该放哪？

这是一个非常关键的架构设计问题：**`joints` 数组不应该放在 `Node` 类里。**

如果你在 `Node` 里放一个 `joints` 数组，会导致逻辑混乱，因为：
1.  **大多数 Node 都不是蒙皮的**：对于石头、树、灯光等节点，这个数组永远是空的，浪费内存。
2.  **职责冲突**：`Node` 的职责是管理场景位置；而 `joints` 数组的职责是管理“蒙皮调色板”。

#### 推荐的类结构设计

```cpp
// 1. 场景节点：通用的、基础的
class Node {
public:
    std::string m_name;
    Vec3 m_translation;
    Quat m_rotation;
    
    Node* m_parent;
    std::vector<Node*> m_children; // 场景层级：大管家
    
    Mesh* m_mesh;
    Skin* m_skin; // 如果不为空，说明此节点是蒙皮实例
};

// 2. 蒙皮组件：连接 Node 和 Skeleton
class Skin {
public:
    Skeleton* m_skeleton; // 指向共享的骨架蓝图
    
    // 【在这里！】存放该实例特有的骨骼节点指针
    // 这个数组的顺序必须与 Skeleton->m_inverseBindMatrices 一一对应
    std::vector<Node*> m_joints; 
};

// 3. 骨架资源：静态的、共享的
class Skeleton {
public:
    std::vector<Mat44> m_inverseBindMatrices;
    std::vector<int>   m_parentIndices;
    std::vector<std::string> m_jointNames;
};
```

#### 为什么 `Skin` 需要持有 `std::vector<Node*> m_joints`？

1.  **快速取值**：在每一帧更新动画时，你需要快速遍历这些 Node 拿到它们的 `GlobalTransform`。
2.  **对应关系**：`m_joints[i]` 的全局矩阵乘以 `Skeleton->m_inverseBindMatrices[i]`，就是送往 GPU 的第 `i` 个矩阵。
3.  **这就是“调色板” (Palette)**：这个数组本质上就是把场景树里散落在遍地的 Node，按照骨架要求的顺序“抓”在一起，形成一个紧凑的列表。

**总结建议：**
-   `Node` 继续做它的“大管家”，管好自己的位移和孩子。
-   **`Skin` 类专门维护那个 `joints` 指针数组**，作为连接“场景 Node”和“蒙皮数学”的桥梁。

---

## 2. glTF 数据结构全景图 (Data Structure Overview)

在 glTF 中，`nodes` 数组中的每个对象是一个通用容器。根据其包含的属性不同，它可以扮演 **Joint (关节)**、**Mesh Instance (模型实例)** 或 **Camera (相机)** 等角色。而 `skins` 数组位于文件的 **Root 层**。

下面的合并示例清晰地展示了 Node 如何通过 `skin` 索引关联到 `skins` 数组中的骨架数据：

### 核心 Schema 与索引关系

```json
{
  "asset": { "version": "2.0" },
  "meshes": [ ... ],
  "nodes": [
    {
      "name": "Hero_Mesh_Instance",
      "mesh": 0,
      "skin": 0,
      "translation": [ 0, 0, 0 ],
      "children": [ 1 ]
    },
    {
      "name": "Bone_Root",
      "children": [ 2, 3 ],
      "translation": [ 0, 1, 0 ],
      "rotation": [ 0, 0, 0, 1 ],
      "scale": [ 1, 1, 1 ]
    }
  ],
  "skins": [
    {
      "name": "Hero_Skeleton",
      "joints": [ 1, 2, 3 ],
      "inverseBindMatrices": 4,
      "skeleton": 1
    }
  ]
}
```

**索引关联说明：**
- `nodes[0].mesh`: 指向 `meshes` 数组索引。
- `nodes[0].skin`: 指向 `skins` 数组索引（此处为 0）。
- `skins[0].joints`: 包含一组索引，指向 `nodes` 数组中作为骨骼的节点。
- `skins[0].inverseBindMatrices`: 指向 `accessors` 索引，获取逆绑定矩阵。

---

### 核心属性深度解析

#### 0. 当一个 Node 同时拥有 `mesh` 和 `skin` 时意味着什么？
这是一个非常关键的概念：**这个 Node 是一个“蒙皮网格实例” (Skinned Mesh Instance)**。

-   **角色**：它是这个角色/物体在场景中的“根部”或“锚点”。
-   **mesh 属性**：告诉引擎“画什么”（顶点坐标、法线、权重等静态数据）。
-   **skin 属性**：告诉引擎“怎么动”（绑定哪套骨架、骨骼索引是谁）。
-   **行为**：引擎在渲染该 Node 时，会提取其关联的 `skin` 中的骨骼变换，并在 Shader 中根据 `mesh` 提供的权重对顶点进行实时形变。

> **注意**：如果一个 Node 只有 `mesh` 没有 `skin`，它就是一个普通的静态物体。

#### 1. 变换属性 (TRS vs. Matrix) —— **互斥关系**
-   **TRS (Translation, Rotation, Scale)**:
    -   最常用，因为 **Animation 直接驱动 TRS 属性**。
    -   `rotation` 必须是四元数 $[x, y, z, w]$。
-   **Matrix**:
    -   一个 $4 \times 4$ 的列主序矩阵。
    -   **规范要求**：如果定义了 `matrix`，则不能定义 `translation`/`rotation`/`scale`；反之亦然。
    -   *注：在处理动画时，通常会将 Matrix 分解为 TRS，或统一将 TRS 合并为 Matrix。*

### 节点身份判定决策树 (Node Identity Decision Tree)

在运行时遍历 `nodes` 数组时，你可以通过以下伪代码逻辑快速判定一个节点的角色：

```cpp
if (node.mesh != -1) {
    if (node.skin != -1) {
        // 【蒙皮模型】
        // 逻辑：读取 skin 索引，获取骨架，在 Shader 中进行蒙皮计算
    } else {
        // 【普通静态模型】
        // 逻辑：直接使用 node 的 Global Transform 渲染即可
    }
} else {
    if (isNodeInAnySkinJoints(nodeIndex)) {
        // 【骨骼节点 / Joint】
        // 逻辑：它不渲染模型，但其变换会影响上面的蒙皮模型
    } else {
        // 【空节点 / Locator / Camera 挂载点】
    }
}
```

**关键判定点归纳：**

1.  **是不是蒙皮物体？**：看 Node 是否**同时**拥有 `mesh` 和 `skin`。
2.  **是不是骨骼？**：看 Node 的索引是否出现在 `skins[i].joints` 数组中。
3.  **为什么 `mesh` 节点通常不作为 `joint`？**：
    - 虽然技术上允许，但在实际工程中，为了逻辑清晰，通常会将“承载模型的节点”和“作为骨骼的节点”分开。
    - 蒙皮模型的 Node 通常是所有骨骼的父节点或者是平级的。

### 核心小结：`skin.joints` 里的索引到底是什么？

这是最容易搞混的地方，请务必记住：**`skin.joints` 数组里的每一个数字，都是指向根层级 `nodes` 数组的索引。**

#### 举个例子：
假设你的 `gltf` 文件长这样：

```json
{
  "nodes": [
    { "name": "Mesh_Node" },   // Index 0
    { "name": "Hip_Bone" },    // Index 1
    { "name": "Leg_Bone" },    // Index 2
    { "name": "Foot_Bone" }    // Index 3
  ],
  "skins": [
    {
      "joints": [ 1, 2, 3 ]
    }
  ]
}
```

在这个例子中：
-   `skin.joints[0]` 的值是 `1`，它指向 `nodes[1]` (Hip_Bone)。
-   `skin.joints[1]` 的值是 `2`，它指向 `nodes[2]` (Leg_Bone)。

#### 为什么要多这一层映射？（重要！）

你可能会问：为什么不让顶点直接引用 Node 索引？为什么要通过 `skin.joints` 转一道手？

1.  **建立“关节调色板” (Joint Palette)**：
    -   Shader 里的 `jointIndices` 属性（如 `0, 1, 2, 3`）其实是 **`skin.joints` 数组的下标**。
    -   顶点说“我受 0 号骨头影响”，意思其实是“我受 `skin.joints[0]` 所指向的那个 Node 影响”。
2.  **减少 Shader 压力**：
    -   一个场景可能有几千个 Node，但一个角色通常只有几十根骨头。
    -   通过 `skin.joints`，我们可以把这几十根骨头连续地排在一起，传给 Shader 一个很小的矩阵数组，而不是把整个场景的几千个矩阵都传过去。

**结论：**
-   **`skin.joints` 的值**：是全局 Node ID。
-   **顶点的 `jointIndex` 属性值**：是 `skin.joints` 数组的局部下标。

---

### 补充：`skin.skeleton` 是干什么的？

在 `skins` 对象中，除了 `joints` 和 `inverseBindMatrices`，你经常会看到一个可选字段 `"skeleton": index`。

#### 它的定义
`skeleton` 指向一个 Node 索引，这个 Node 被视为 **骨架层次结构的根节点 (Root of the Hierarchy)**。

#### 它的作用
1.  **确定搜索范围**：它告诉引擎，所有的 `joints` 节点都在这个 `skeleton` 节点及其子树之下。这有助于引擎快速定位骨架在场景图中的位置。
2.  **空间基准 (Common Ancestor)**：在计算蒙皮所需的全局矩阵时，`skeleton` 节点通常被作为“公共祖先”。如果蒙皮模型的 Node 与骨架 Root Node 不在同一个层级，这个字段能帮助引擎理顺变换链。
3.  **动画限定**：某些引擎会利用这个字段来限定动画的应用范围，确保“跑步动画”只作用于这个 `skeleton` 下的骨头，而不会误伤到场景里的其他物体。

#### 它是“没用”的吗？
从某种意义上说，**在 90% 的简单模型中，它确实可以省略**。但它在以下几种特殊场景中具有不可替代的作用：

1.  **性能加速 (Optimization)**：
    - 如果没有这个字段，引擎必须遍历所有的 `joints`，通过回溯父节点来计算出它们的“共同祖先”。
    - 在拥有数千个节点的复杂场景中，直接给引擎一个 `skeleton` 索引可以省去这次耗时的搜索。
2.  **多根骨架 (Disambiguation)**：
    - 某些复杂的模型可能有多个独立的骨骼分支（例如一个角色的两根飘带是独立的骨骼链）。
    - `skeleton` 明确指定了这几个分支在场景树中的汇合点，确保坐标空间变换的唯一性。
3.  **非父子关系的骨架**：
    - glTF 允许 `joints` 列表中的节点在层级上并不是严格的父子关系。
    - 在这种极端情况下，如果没有 `skeleton` 指明根节点，引擎将彻底失去坐标基准。

**结论**：你可以把它看作是一个 **“保险协议”**。虽然大多数时候引擎能自己猜出来，但显式指定它能避免在复杂场景下产生逻辑歧义。

---

### 深度解析：`inverseBindMatrices` (IBM)

在 `skins` 对象中，你会看到类似 `"inverseBindMatrices": 6` 的字段。这个整数 `6` 是一个 **Accessor (访问器) 的索引**。

#### 1. 它是如何获取的？
- 引擎会根据这个索引去 Root 层的 `accessors` 数组中找到第 6 个 Accessor。
- 这个 Accessor 会告诉你如何从二进制文件（`.bin`）中读取出一组 $4 \times 4$ 的矩阵数据。
- **数量匹配**：这个 Accessor 包含的矩阵数量必须与 `joints` 数组的长度**完全一致**。

#### 2. 它的数学意义是什么？（为什么需要它？）
IBM 被称为“逆绑定矩阵”，它的作用是 **“抵消变换” (Un-transform)**。

想象一下：
- 模型的顶点最初是在“模型空间”定义的。
- 骨头（Joint）在模型空间也有一个位置（比如手肘在 `(0, 5, 0)`）。
- 如果你直接让顶点随骨头旋转，顶点会绕着“世界原点”转，而不是绕着“手肘”转。

**IBM 的工作就是**：把顶点从“模型空间”拉回到“骨骼的局部空间”（也就是让骨骼重新回到原点）。
- **公式逻辑**：`InverseBindMatrix = inv(GlobalTransform_at_BindPose)`。
- 它记录了在模型绑定（通常是 T-Pose）那一刻，骨骼在世界/模型空间中的**反向变换**。

#### 3. 蒙皮的核心计算链路
在 Shader 中，每一帧我们要算的其实是：
1. **回到过去**：用 `IBM` 把顶点拉回骨骼局部空间。
2. **回到现在**：用当前的 `GlobalTransform` 把顶点推到当前骨骼应该在的位置。

> **计算公式**：`SkinningMatrix = CurrentGlobalTransform * InverseBindMatrix`

**结论**：如果没了 `inverseBindMatrices`，你的模型在动画开始的那一刻就会“瞬间爆炸”，因为所有顶点都会尝试绕着场景中心旋转，而不是绕着自己的关节旋转。

### 如何在运行时判断一个 Node 是不是 Joint？

这是一个非常实操的问题。基于我们之前的映射表，判断逻辑如下：

#### 1. 针对特定骨架 (Specific Skeleton)
如果你想知道 Node 50 是不是**当前这个角色**的骨头：
- **逻辑**：检查 `m_nodeToJointIndex` 这个 Map。
- **伪代码**：
  ```cpp
  if (skeleton->m_nodeToJointIndex.count(nodeID)) {
      // 它是这个骨架的一根骨头！
      int jointIdx = skeleton->m_nodeToJointIndex[nodeID];
  }
  ```

#### 2. 全局判断 (Global Check)
如果你想在遍历整个场景时知道 Node 50 是不是**任何一个**骨架的骨头：
- **推荐做法**：在加载 Pass 2（处理 Skins）时，给 Node 类加一个布尔标记 `m_isJoint`。
- **逻辑**：只要 Node 的索引出现在任何一个 `skin.joints` 数组里，就将其设为 `true`。

### 再次强调：Joint 是一种“角色”而非“类型”

-   **Node 本身不知道自己是不是 Joint**。
-   在 glTF 文件的 `nodes` 数组里，它只是一个普通的节点。
-   **只有当你读了 `skins` 数组后**，你才知道原来 Node 1, 2, 3 被点名去当骨头了。

**所以，最稳妥的判定逻辑是：**
“被 `skin.joints` 引用了的 Node，就是 Joint。”

---

## 3. 引擎解析逻辑流 (Logic Flow)

当你（或引擎）遇到一个带蒙皮的模型时，查找顺序如下：

1.  **Scene 入口**：在 `nodes` 数组中发现一个同时带 `mesh` 和 `skin` 的 Node。
2.  **识别身份**：读取 `node.skin` 索引。
3.  **跳转 Skin**：根据索引找到 `skins[i]`，拿到 `joints` 列表（这里存的是一串 Node 索引）。
4.  **收集骨骼状态**：遍历 `joints` 列表中的每个索引，去 `nodes` 数组中找到对应的骨骼 Node，读取它们当前的 **TRS (Global Transform)**。
5.  **读取 IBM**：从 `skins[i].inverseBindMatrices` 指向的 Accessor 中读取每个关节的逆绑定矩阵（通常在加载时只读一次）。
6.  **计算 Palette**：在 CPU 或 GPU 中计算 $GlobalTransform \cdot IBM$，传给 Shader 渲染。

---

## 5. 动画驱动流程 (Animation Driving Flow)

当你播放一个如 "Running" 的动画时，数据是如何从动画片段传递到骨骼并最终改变模型形状的？

### 动画数据结构 (glTF Animation)

在 glTF 中，一个动画剪辑由多个 **Channel (通道)** 组成，每个通道将 **Sampler (采样器)** 的数据应用到指定的 **Node** 上。

```json
{
  "animations": [
    {
      "name": "Running",
      "channels": [
        {
          "sampler": 0,
          "target": {
            "node": 1,
            "path": "rotation"
          }
        }
      ],
      "samplers": [
        {
          "input": 5,
          "interpolation": "LINEAR",
          "output": 6
        }
      ]
    }
  ]
}
```

**关键概念解析：**
- **Input (时间轴)**: 存储关键帧时间点（如 0.0s, 0.5s, 1.0s）的 Accessor。
- **Output (变换值)**: 存储对应时间点的 TRS 数据（如旋转四元数）的 Accessor。
- **Interpolation (插值)**: 决定如何计算两个关键帧之间的时间点。
    - `LINEAR`: 线性插值（最常用）。
    - `STEP`: 阶梯式（无插值）。
    - `CUBICSPLINE`: 三次样条插值（更平滑）。
- **Target (目标)**: 指定该动画数据要修改哪个 Node 的哪个属性（`translation`, `rotation`, `scale`, `weights`）。

### 运行时计算逻辑

1.  **确定当前时间 ($T_{current}$)**: 根据游戏运行时间，计算当前动画播放到了第几秒。
2.  **寻找关键帧 (Sampling)**: 在 `input` 数组中找到 $T_{current}$ 落在哪个区间（例如 $T_i$ 和 $T_{i+1}$ 之间）。
3.  **插值计算 (Interpolation)**: 
    - 根据 $T_i$ 和 $T_{i+1}$ 处的值，计算出 $T_{current}$ 对应的插值结果。
    - 如果是旋转，通常使用 **Slerp (球面线性插值)**。
4.  **更新 Node 局部变换**: 将计算出的结果写入对应的 `node.rotation` 或 `node.translation`。
5.  **矩阵级联更新 (Hierarchy Update)**: 
    - 动画只更新了 Node 的 **Local TRS**。
    - 需要从根节点开始，递归计算每个节点的 **Global Transform**。
    - 公式：`Global = Parent.Global * Local`。
6.  **计算蒙皮矩阵**: 按照上一节的“逻辑流”，将最新的 `Global Transform` 与 `Inverse Bind Matrix` 相乘，得到传给 Shader 的 `jointMatrix`。

---

## 6. 引擎实现：Pose 数据结构 (Engine Pose Structure)

在实际的引擎代码中，一个 `Pose` 类通常采用 **SoA (Structure of Arrays)** 的形式存储，以便于进行批量插值和矩阵计算。你提供的结构是非常标准且高效的实现：

### 典型的 C++ Pose 类成员

```cpp
struct Pose {
    std::vector<Vec3>  m_translations;
    std::vector<Vec4>  m_rotations;
    std::vector<Vec3>  m_scales;

    std::vector<Mat44> m_localTransforms;
    std::vector<Mat44> m_worldTransforms;

    std::vector<int>   m_parentIndices;
};
```

### 各成员的作用与意义

1.  **Local TRS (translations, rotations, scales)**:
    - 存储从动画采样器 (Sampler) 插值得到的局部变换。
    - 为什么分开存？因为在**动画混合 (Blending)** 时，我们需要对平移、旋转、缩放分别进行线性插值 (Lerp/Slerp)，直接插值矩阵会产生错误的缩放结果。
2.  **m_localTransforms**:
    - 将 TRS 合并后的 $4 \times 4$ 局部矩阵。
    - 公式：`LocalMatrix = T * R * S`。
3.  **m_worldTransforms**:
    - 经过父子层级级联计算后的全局/模型空间矩阵。
    - 只有拿到这个矩阵，才能与 `InverseBindMatrix` 相乘。
4.  **m_parentIndices**:
    - 核心层级数据。存储每个节点的父节点索引。
    - **算法逻辑**：
        - 必须保证 `parentIndex < childIndex`（即父节点总是在数组前面）。
        - 这样只需要一次线性循环即可完成全局变换更新：
          `worldTransforms[i] = worldTransforms[parentIndices[i]] * localTransforms[i]`。

### 总结：Pose 的生命周期

1.  **Sampling**: 根据时间采样动画数据，填充 `m_translations`, `m_rotations`, `m_scales`。
2.  **Local Sync**: 将 TRS 合并到 `m_localTransforms`。
3.  **Global Sync**: 利用 `m_parentIndices` 将局部矩阵级联为 `m_worldTransforms`。
4.  **Skinning**: 将 `m_worldTransforms` 与 `IBM` 相乘，发送给 GPU。

---

## 7. 最佳实践：加载顺序 (Recommended Loading Sequence)

针对你问的“什么时候找 joints”，最推荐的做法是 **“分多步走”**。不要在第一次遍历 nodes 时就去处理蒙皮，因为那时候你可能还没读到 skins 数组。

### 推荐的加载步骤

1.  **Pass 1：加载所有 Nodes (Scene Graph)**
    - 遍历 `nodes` 数组，创建所有 Node 对象。
    - 建立好父子层级（Children）。
    - *此时不处理 mesh 或 skin。*

2.  **Pass 2：加载 Root 层的 `skins` 数组 (Skeleton Init)**
    - **直接遍历最外层的 `skins` 数组**，而不是遍历 nodes。
    - 对于每一个 `skins[i]`：
        - 根据 `joints` 索引去 Pass 1 存好的 nodes 里找节点。
        - 计算该 Skeleton 的 `m_parentIndices`。
        - 加载并存储 `InverseBindMatrices`。
    - *目的：为每个 Skin 创建一个唯一的“骨架模板”。*

3.  **Pass 3：关联蒙皮实例 (Instance Linking)**
    - 遍历所有的 `nodes`。
    - 如果发现 `node.skin != -1`：
        - 将该 Node 关联到 Pass 2 中创建好的第 `i` 个骨架模板。
        - 此时这个 Node 就正式成为了一个“蒙皮网格实例”。

### 为什么要先遍历 `skins` 数组，而不是从 node 往回找？

-   **一对多关系**：如果 100 个 Node 使用同一个 Skin，你从 node 往回找就会重复检查 100 次。直接遍历 root 层的 `skins` 数组，可以确保每个骨架只被初始化一次。
-   **效率更高**：`skins` 数组通常很短（可能只有几个），而 `nodes` 数组可能成千上万。先处理短的数组建立“模板”，再处理长的数组进行“挂载”，效率更高。

### 核心区别：定义 (Definition) vs. 使用 (Usage)

为了理清你的困惑，我们可以把 glTF 的这种设计类比为“蓝图”与“建筑”：

| 位置 | 角色 | 类比 | 数量 |
| :--- | :--- | :--- | :--- |
| **Root 层的 `skins` 数组** | **定义 (Definition)** | 骨架的**蓝图** (Blueprint) | 少（通常每个角色一套） |
| **Node 里的 `skin` 索引** | **使用 (Usage)** | 根据蓝图盖出来的**建筑** (Instance) | 多（可以有多个兵用同一套蓝图） |

#### 为什么不从 Node (使用端) 开始初始化？

1.  **避免“多对一”的重复检查**：
    - 如果你从 Node 开始找，你每读到一个兵都要问一句：“这个 Skin 0 我初始化过了吗？”。
    - 如果直接从 `skins` 数组开始，你只需要按顺序把蓝图全部打印出来（初始化 `Pose` 对象），后面 Node 用的时候直接拿现成的。

2.  **数据结构的完整性**：
    - `skins` 对象里包含了该骨架的所有核心信息：`joints` 列表和 `inverseBindMatrices`。
    - Node 里只有一个孤零零的数字索引。
    - **先处理 `skins`** 意味着你先构建了引擎的“动画系统”；**再处理 `nodes`** 则是把场景里的物体挂载到这个系统上。

#### 总结：最清晰的代码逻辑

-   **加载阶段**：扫一遍 `skins` 数组 -> 为每个 Skin 创建一个 `Skeleton` 或 `Pose` 资源对象。
-   **解析节点阶段**：看到 `node.skin = 5` -> 顺着索引直接把这个 Node 的蒙皮指针指向 `Skeletons[5]`。

这样你的加载器逻辑是**单向、线性且无冗余**的。

---

## 8. 引擎实现：Pose 数据结构 (Engine Pose Structure)


在将 glTF 加载到引擎时，我们需要将分散的 `nodes` 拍平（Flatten）到 `Pose` 的线性数组中。

### 如何构建 `m_parentIndices`？

1.  **确定 Joint 顺序**：通常按照 `skins[i].joints` 数组的顺序来分配 `Pose` 里的索引。
    - `Pose[0]` 对应 `nodes[joints[0]]`
    - `Pose[k]` 对应 `nodes[joints[k]]`
2.  **建立节点反向查找表**：创建一个 `std::map<int, int> gltfNodeToPoseIndex`。
    - 键是 glTF 的原始 Node 索引。
    - 值是该节点在 `Pose` 数组中的新位置。
3.  **寻找父节点**：
    - 遍历 `joints` 列表中的每个节点 $N$。
    - 在 glTF 中找到它的父节点索引 $P$。
    - 通过查找表找到 $P$ 对应的 Pose 索引，存入 `m_parentIndices`。
    - 如果父节点不在 `joints` 列表中（通常是根节点），则 `m_parentIndices = -1`。

### 为什么用 `parentIndex` 而不是直接存 Node 指针？

-   **缓存友好 (Cache Locality)**：数组在内存中是连续的，CPU 预取（Prefetch）效率极高。
-   **计算简洁**：更新全局变换时，只需一个循环遍历数组，不需要进行复杂的树形递归。
-   **解耦**：`Pose` 类只负责数学运算，不需要了解 `glTF Node` 对象的复杂结构。

### 运行时更新逻辑示例

```cpp
void UpdateWorldTransforms() {
    for (int i = 0; i < m_numJoints; ++i) {
        int parentIdx = m_parentIndices[i];
        if (parentIdx == -1) {
            m_worldTransforms[i] = m_localTransforms[i];
        } else {
            // 依赖关系：父节点必须在子节点之前已经计算过
            m_worldTransforms[i] = m_worldTransforms[parentIdx] * m_localTransforms[i];
        }
    }
}
```

### 重点澄清：`parentIndex` 是谁的索引？

这是一个极易出错的细节：在 `Skeleton` 或 `Pose` 类中，**`m_parentIndices` 存储的是【局部骨骼索引】，而不是【全局 Node 索引】。**

#### 为什么不存全局 Node 索引？
1.  **紧凑性 (Compactness)**：一个场景可能有 10,000 个 Node，但一个角色通常只有 50 个骨头。如果用全局索引，你的数组会非常稀疏，浪费内存。
2.  **线性计算 (Linear Update)**：在 `m_worldTransforms` 的更新循环中，我们需要保证 `worldTransforms[parentIndex]` 已经算好了。如果用局部索引（0, 1, 2...），我们可以非常容易地进行线性遍历。

#### 索引映射示例
假设一个 glTF 的结构如下：

-   **Nodes 数组**: `[ Node0(Mesh), Node1(Hip), Node2(Spine), Node3(Camera) ]`
-   **Skin.joints**: `[ 1, 2 ]` (表示这个骨架只有两根骨头，分别是 Node1 和 Node2)

**在你的 `Skeleton` 对象中：**
-   **Joint 0** (对应 Node 1): `parentIndex = -1` (它是根)
-   **Joint 1** (对应 Node 2): `parentIndex = 0` (**指向的是 Joint 0，而不是 Node 0**)

#### 结论
-   **全局 Node 索引**：用于加载时寻找物体。
-   **局部 Joint 索引 (0 ~ N-1)**：用于运行时的动画混合、级联计算和 Shader 传参。

我们在加载阶段的工作，就是把 glTF 这种“大世界坐标系”下的复杂引用，通过一个查找表转换成 `Skeleton` 这种“小圈子”里的简单局部索引。

### 构建层级：向上搜索策略 (The Search-Up Strategy)

当你确定 Node 50 是一个 Joint 时，你不需要向下寻找它所有的子节点。相反，为了构建 `m_parentIndices`，你应该 **向上寻找它的“骨骼父亲”**。

#### 为什么不向下找？
- **子树太大**：一个骨骼节点下面可能挂着几百个非骨骼节点（比如饰品、相机、挂载点）。向下找会非常低效。
- **逻辑复杂**：一个节点可能有多个孩子，你需要处理递归分支。

#### 推荐的“向上搜索”算法
对于 `skin.joints` 列表中的每一个节点 $N$：

1.  **向上走一步**：找到 $N$ 在场景树中的父节点 $P$。
2.  **身份核实**：检查 $P$ 是否也在 `skin.joints` 列表里？
    -   **如果是**：恭喜！$P$ 就是 $N$ 在骨架里的“直系父亲”。记录下 $P$ 的局部索引，填入 `m_parentIndices`。
    -   **如果不是**：继续往上走，找 $P$ 的爸爸，重复步骤 2。
3.  **终止条件**：
    -   找到了一个属于 `joints` 列表的祖先。
    -   或者撞到了场景根节点（或 `skin.skeleton` 指定的根节点）。此时说明 $N$ 是一根“根骨头”，`m_parentIndices = -1`。

#### 这种做法的好处
- **路径唯一**：每个节点只有一个父节点，向上走是一条直线，逻辑极其简单。
- **自动忽略无关节点**：如果骨骼 A 和骨骼 B 之间隔了几个普通 Node（比如作为缓冲的空节点），这个算法能自动跳过它们，直接建立 A 和 B 的父子关系。

**总结：**
不要问“我下面有哪些骨头？”，而要问 **“离我最近的、当骨头的祖先是谁？”**。

---

## 8. 映射之桥：连接 Pose 与 Node (The Index Bridge)

为了让引擎能在“紧凑的数学数组”和“庞大的场景树”之间自由切换，你需要两个核心映射表。我们将它们存入 `Skeleton` 类中。

### 1. 从 Pose 找 Node (Index -> ID)
**用途**：当你在更新 `m_worldTransforms[i]` 时，你可能需要知道这根骨头的原名或它在场景里的实时状态。
- **数据结构**：`std::vector<int> m_jointNodeIndices;`
- **含义**：`m_jointNodeIndices[i]` 存储的是“坐在第 `i` 号位置的骨头，它在 `nodes` 大地图里的原始索引”。

### 2. 从 Node 找 Pose (ID -> Index)
**用途**：**最关键用途是处理动画**。动画数据说“我要修改 Node 50 的旋转”，你需要立刻知道 Node 50 坐在 `Pose` 里的哪个位置。
- **数据结构**：`std::map<int, int> m_nodeToJointIndex;`
- **含义**：输入 Node 索引 `50`，返回他在 `Pose` 数组里的下标（比如 `2`）。

### 更新后的 Skeleton 类逻辑

```cpp
class Skeleton {
public:
    // --- 映射表 ---
    // 长度为 N (骨骼数)
    std::vector<int> m_jointNodeIndices; 
    
    // 键为 NodeID，值为 0~N-1
    std::map<int, int> m_nodeToJointIndex;

    // --- 核心数学数据 ---
    std::vector<Mat44> m_inverseBindMatrices;
    std::vector<int>   m_parentIndices;
};
```

### 运行时：动画是如何应用到 Pose 的？

假设一个动画通道的目标是 `node: 50`，属性是 `rotation`：

1.  **查询**：`int jointIdx = skeleton->m_nodeToJointIndex[50];`
2.  **定位**：发现 `jointIdx` 是 `2`。
3.  **写入**：将插值后的四元数写入 `currentPose.m_rotations[2]`。

### 总结：你的直觉是对的

当你拿到一个 `poseIndex`（比如 `i`），它确实代表了场景里的某一个具体的 Node。
- 通过 `m_jointNodeIndices[i]`，你能找回那个 Node 的“真身”。
- 通过 `m_parentIndices[i]`，你能找回它在“剧组”里的爸爸。

这两个数组就像是你的导航地图，让你在“数学运算”和“业务逻辑”之间不会迷路。

---

## 9. Skeleton (模板) vs. Pose (状态)

在成熟的引擎架构中，我们会把“骨架的定义”和“骨架的当前状态”分开。`Skeleton` 是只读的资源模板，而 `Pose` 是每个实例特有的动态数据。

### Skeleton 类 (静态资源)

`Skeleton` 存储的是从 glTF 文件里读出来的、不会随时间改变的数据。

```cpp
class Skeleton {
public:
    // 逆绑定矩阵：从模型空间转到骨骼局部空间
    std::vector<Mat44> m_inverseBindMatrices;

    // 骨架层级结构：定义谁是谁的爸爸
    std::vector<int>   m_parentIndices;

    // 骨骼名称：用于按名查找动画或调试
    std::vector<std::string> m_jointNames;

    // 默认姿态：通常是 T-Pose 或加载时的初始姿势
    Pose m_bindPose;
};
```

### Pose 类 (动态状态)

`Pose` 存储的是当前这一帧，骨头到底在哪里。

```cpp
struct Pose {
    // 局部变换：每一帧被动画修改的数据
    std::vector<Vec3> m_translations;
    std::vector<Vec4> m_rotations;
    std::vector<Vec3> m_scales;

    // 级联计算出的全局矩阵：传给 Shader 用的数据
    std::vector<Mat44> m_worldTransforms;
};
```

### 它们如何协作？

当你渲染一个英雄角色时，引擎的操作逻辑如下：

1.  **资源引用**：该 Node 持有一个 `Skeleton*` 指针（指向共享的蓝图）和一个 `Pose` 对象（自己独有的状态）。
2.  **动画更新**：动画系统插值出新的 TRS，填充到 `Pose` 的 `m_translations/rotations` 中。
3.  **计算全局矩阵**：利用 `Skeleton->m_parentIndices` 将 `Pose` 里的局部变换级联成 `m_worldTransforms`。
4.  **最终计算 (Matrix Palette)**：
    -   **公式**：`SkinningMatrix[i] = Pose.m_worldTransforms[i] * Skeleton->m_inverseBindMatrices[i]`。
    -   这一步算出来的 `SkinningMatrix` 数组才是真正送进显卡 Shader 的数据。

### 总结：为什么要分开？

-   **节省内存**：如果你有 100 个士兵，你只需要一份 `Skeleton` 数据（IBM 矩阵非常占内存），而每个士兵只需要自己的一份轻量级 `Pose`。
-   **逻辑清晰**：`Skeleton` 负责“骨头长什么样，怎么连”，`Pose` 负责“骨头现在往哪摆”。

---

## 10. Skeleton vs. Node: 深度对比

这是引擎开发中最容易产生困惑的两个概念。简单来说：**Node 是场景中的“实体”，而 Skeleton 是这些实体协作的“逻辑蓝图”。**

### 核心差异对比表

| 特性 | Node (节点) | Skeleton (骨架资源) |
| :--- | :--- | :--- |
| **本质** | 场景图中的一个**点/容器** | 一组骨骼的**拓扑结构与数学定义** |
| **关注点** | **“我在哪？”** (Where) | **“我怎么变？”** (How) |
| **数据内容** | TRS、Children、Mesh 引用 | IBM 矩阵、父子索引、骨骼名 |
| **生命周期** | 随场景加载/卸载 | 作为资源常驻内存，可被多处引用 |
| **数量关系** | 一个角色有几十个 Node 作为骨头 | 整个角色群共享一个 Skeleton 资源 |

### 它们的关系：角色、演员与剧本

为了方便理解，我们可以打个比方：

1.  **Skeleton (剧本)**：规定了“这出戏有 20 个角色（骨头），他们谁是谁的儿子，他们的初始站位（IBM）在哪里”。
2.  **Node (演员)**：场景里真实的节点。有些 Node 被选为“演员”，分配到了 Skeleton 里的角色 ID（比如 Node 5 演“左手”，Node 6 演“左小臂”）。
3.  **Skin (导演)**：把“演员”（Nodes）和“剧本”（Skeleton）缝合在一起。它告诉引擎：“用这组 Node 按照这个 Skeleton 的规则来驱动这个 Mesh”。

### 关键点：Node 可以是 Skeleton 的一部分

在 glTF 的蒙皮逻辑中：
-   **骨骼节点 (Joint Node)**：它首先是一个普通的 `Node`，拥有 TRS 和父子关系。
-   **身份转变**：当它的索引出现在 `skin.joints` 数组中时，它在逻辑上就成了 `Skeleton` 的一根“骨头”。

**引擎开发建议：**
-   在你的 `Node` 类里，不要存 IBM 或父子索引。
-   把这些静态的、属于“规则”的数据全部抽离到 `Skeleton` 类中。
-   `Node` 只需要管好自己的 **Local TRS**，剩下的交给 `Skeleton` 去计算。

---

## 11. 蒙皮逻辑中的 Node 角色：它们真的“没关系”吗？

绝对不是！**蒙皮逻辑完全是建立在 Node 数据之上的。** 它们之间的关系是典型的“生产者”与“消费者”：

### 协作分工表

| 组件 | 角色 | 贡献的数据 | 缺少它的后果 |
| :--- | :--- | :--- | :--- |
| **Node (节点)** | **生产者** | **实时全局变换 (Global Matrix)** | 骨架是死的，没有任何动作 |
| **Skin (蒙皮组件)** | **加工者** | **骨骼列表 (Joints)、逆绑定矩阵 (IBM)** | 动作无法应用到模型表面，模型变“硬” |
| **Mesh (网格)** | **消费者** | **顶点坐标、权重 (Weights)、索引 (Indices)** | 有动作但看不见任何形体 |

### 为什么你会觉得“没关系”？

可能是因为在**代码实现层级**上，我们提倡“解耦”：
- **Node 不知道自己在被谁用**：Node 只管在场景里转动、移动。它不关心自己是作为一根“手指”还是一个“路灯”。
- **Skin 负责“盯着” Node**：Skin 就像一个观察者，它手里拿着一张单子（`m_joints`），每帧去问这些 Node：“嘿，你现在的全局矩阵是多少？快给我，我要算蒙皮矩阵了！”。

### 总结：蒙皮逻辑的“三位一体”

当你看到一个英雄在跑动时，幕后的逻辑是这样的：

1.  **Node 逻辑**：负责把父子关系级联起来，算出每一根骨头的 `GlobalTransform`。
2.  **Skin 逻辑**：
    -   把 Node 算好的 `GlobalTransform` 拿过来。
    -   乘以自己存的 `InverseBindMatrix`。
    -   打包成 `Matrix Palette` 传给显卡。
3.  **渲染逻辑**：GPU 拿到这些矩阵，根据顶点上的权重，把模型“揉”成正确的形状。

**结论**：**Skin 逻辑的核心就是“搬运并加工 Node 的变换数据”**。如果没有 Node 提供实时的坐标，Skin 逻辑就是无米之炊。

---

## 12. Skin vs. Skeleton: 资源与实例的关系

这是蒙皮系统的最后一块拼图：**`Skeleton` 是静态的“资源” (Resource)，而 `Skin` 是动态的“实例” (Instance/Component)。**

### 深度对比

| 特性 | Skeleton (骨架资源) | Skin (蒙皮实例/组件) |
| :--- | :--- | :--- |
| **角色** | **蓝图 (Blueprint)** | **活的物体 (Live Instance)** |
| **存储位置** | 资源管理器 (ResourceManager) | 场景中的特定 Node 上 |
| **包含内容** | 逆绑定矩阵 (IBM)、父子索引 | 指向骨骼 Node 的指针数组 (`m_joints`) |
| **共享性** | **高度共享**。100 个小兵共用一个 | **独占**。每个小兵都有自己的 Skin 实例 |
| **内存开销** | 较大（存储大量矩阵和字符串） | 极小（只存储一堆指针/索引） |

### 它们是如何关联的？

在 C++ 类设计中，它们通常是 **1:N** 的引用关系：

```cpp
// 资源类：整个游戏生命周期内，每种角色只有一份
class Skeleton {
public:
    std::vector<Mat44> m_inverseBindMatrices;
    std::vector<int>   m_parentIndices;
    // ... 其他静态数据
};

// 组件类：场景里每个角色都持有一个
class Skin {
public:
    // 指向它所使用的资源
    Skeleton* m_skeleton; 

    // 这个实例特有的、对应的场景节点
    // 数组顺序必须与 m_skeleton->m_inverseBindMatrices 一致
    std::vector<Node*> m_joints; 

    // 每一帧算出的最终矩阵，发往 GPU
    std::vector<Mat44> m_matrixPalette; 
};
```

### 为什么一定要这么分？

1.  **内存极限优化**：
    - 一个复杂的骨架可能有 100 根骨头，对应的 IBM 矩阵就是 $100 \times 64 = 6.4\text{KB}$。
    - 如果你把这些数据直接存在 `Skin` 里，场景里有 1000 个小兵，光 IBM 就要占 $6.4\text{MB}$。
    - 如果存在 `Skeleton` 里共享，1000 个小兵只需要 $6.4\text{KB}$。
2.  **加载效率**：加载 glTF 时，你只需要解析一次 `skins` 数据生成 `Skeleton` 资源，后面实例化小兵时直接关联指针即可。

### 总结：你的开发流程

1.  **加载阶段**：
    - 读 glTF 的 `skins` 数组 -> 创建一个全局唯一的 `Skeleton` 资源。
2.  **实例化阶段**：
    - 为每个带皮的 Node 创建一个 `Skin` 对象。
    - 让 `Skin->m_skeleton` 指向刚才加载的资源。
    - 根据 `skins[i].joints` 的索引，把场景里的 Node 指针填进 `Skin->m_joints`。
3.  **渲染阶段**：
    - `Skin` 拿着 `m_joints` 的全局坐标，配上 `m_skeleton` 的 IBM，算出结果。

---

## 13. 蒙皮架构“三剑客”：Skeleton, Pose, Skin

为了让你的引擎架构达到工业级水平，你需要这三个类各司其职。它们之间的关系是：**一个 Skeleton (剧本) 对应多个 Skin (演出)，每个 Skin 拥有一套自己的 Pose (动作状态)。**

### 终极类结构设计

```cpp
// 1. 【剧本】Skeleton (资源类)
// 全局唯一，只读。存储骨架的拓扑结构。
class Skeleton {
public:
    std::vector<Mat44> m_inverseBindMatrices; // 核心：逆矩阵
    std::vector<int>   m_parentIndices;       // 核心：层级
    std::vector<std::string> m_jointNames;
};

// 2. 【台词】Pose (数据结构)
// 纯数学容器。存储某一帧骨骼的位姿。
struct Pose {
    std::vector<Vec3>  m_translations;
    std::vector<Vec4>  m_rotations;
    std::vector<Vec3>  m_scales;
    std::vector<Mat44> m_worldTransforms;
};

// 3. 【演出】Skin (组件类/实例)
// 每个角色一个。负责把剧本、动作和场景里的 Node 缝合在一起。
class Skin {
public:
    Skeleton* m_skeleton;      // 引用的资源
    Pose      m_currentPose;   // 这一帧我自己的动作状态
    
    // 该实例对应的场景 Node 指针数组
    // 动画系统更新这些 Node，Skin 每一帧去这些 Node 里取数据
    std::vector<Node*> m_joints; 

    // 发往 GPU 的最终矩阵调色板
    std::vector<Mat44> m_matrixPalette; 
};
```

### 为什么这个架构是“无敌”的？

1.  **极度省钱 (Memory)**：
    - `Skeleton` 存了大头（IBM 矩阵），被所有人共享。
    - `Skin` 只存了 Node 指针，非常轻量。
2.  **极度解耦 (Decoupling)**：
    - 动画系统只管去更新 `Node`。
    - `Skin` 只管去 `Node` 里拿数据。
    - 它们互不干涉，你可以随时给角色换一个 `Skeleton` 蓝图（实现动态换装）。
3.  **极度高效 (Performance)**：
    - 更新 `worldTransforms` 时，利用 `Skeleton->m_parentIndices` 只需要一个线性 `for` 循环。
    - 计算 `matrixPalette` 时，只需一次线性 `for` 循环把 `worldTransform * IBM` 即可。

### 总结：你的 C++ 实现之路

1.  **`Skeleton`** 是你在加载时创建的 **Asset**。
2.  **`Pose`** 是你在计算动画时使用的 **Math Buffer**。
3.  **`Skin`** 是你在场景里每个角色身上挂载的 **Component**。

当你把这三个类写完并连通时，你的 3D 引擎就已经具备了处理复杂角色动画的能力。

---

## 14. 关联之路：Skin 是如何找到 Skeleton 的？

在 glTF 文件中，它们通过 **Index (索引)** 关联；但在你的引擎里，它们通过 **Pointer (指针)** 关联。这个转换发生在加载阶段。

### 加载时的资源池 (Resource Pool)

在加载 glTF 时，你需要准备一个临时的容器来存放解析出来的资源：

```cpp
// 临时存储所有加载好的资源
std::vector<Skeleton*> allSkeletons; 
std::vector<Node*>     allNodes;
```

### 具体的连接流程

#### 1. 建立资源 (Pass 2)
遍历 glTF 的 `skins` 数组，每读到一个 skin，就创建一个 `Skeleton` 对象并存入 `allSkeletons`。
- `skins[0]` -> `allSkeletons[0]`
- `skins[5]` -> `allSkeletons[5]`

#### 2. 寻找归宿 (Pass 3)
遍历 `nodes` 数组。当你读到 Node 50 时，发现它包含 `"skin": 5`：

```cpp
// 发现一个需要蒙皮的 Node
if (gltfNode.skinIndex != -1) {
    // 1. 创建 Skin 组件
    Skin* newSkin = new Skin();
    
    // 2. 【关键】通过索引直接找到对应的 Skeleton 指针
    int skinIdx = gltfNode.skinIndex;
    newSkin->m_skeleton = allSkeletons[skinIdx];
    
    // 3. 顺便把骨骼 Node 指针也填好
    for (int jointNodeIdx : allSkeletons[skinIdx]->m_jointNodeIndices) {
        newSkin->m_joints.push_back(allNodes[jointNodeIdx]);
    }
    
    // 4. 将 Skin 挂载到 Node 上
    myNode50->m_skin = newSkin;
}
```

### 总结：联系的纽带就是“加载器”

1.  **Index 是地图上的坐标**：glTF 说“去 5 号柜台拿蓝图”。
2.  **Pointer 是手里的原件**：你的加载器跑去 5 号柜台，把蓝图拿出来，塞进了 `Skin` 的手里。

**以后渲染时：**
`Skin` 不需要问“我是谁的”，它低头看看手里的 `m_skeleton` 指针，就知道所有的逆矩阵和层级关系了。

这样，你就把一个**静态的 JSON 文件**变成了**动态的内存对象网络**。

---

## 15. 常见蒙皮算法对比

### 线性混合蒙皮 (Linear Blend Skinning, LBS)
这是最常用的蒙皮算法，如上一节公式所示。
- **优点**：计算简单，GPU 开销极低。
- **缺点**：**糖果纸效应 (Candy Wrapper Effect)**。在关节大角度旋转（如手肘、膝盖）时，体积会发生明显的塌陷和扭曲。

### 双四元数蒙皮 (Dual Quaternion Skinning, DQS)
为了解决 LBS 的体积塌陷问题，使用双四元数来插值旋转和平移。
- **优点**：能够完美保持关节处的体积，避免塌陷。
- **缺点**：
    - 计算开销比 LBS 高（Shader 中需要处理四元数运算）。
    - 难以处理缩放（Scaling）变换。
    - 在某些极端折叠情况下可能产生“鼓包”。

---

## 6. 渲染工程实践

### CPU Skinning vs. GPU Skinning

| 特性 | CPU Skinning | GPU Skinning (主流) |
| :--- | :--- | :--- |
| **计算位置** | 每一帧在 CPU 端计算顶点位置 | 在 Vertex Shader 中实时计算 |
| **带宽压力** | 高（每帧需传输全量动态顶点数据） | 低（仅传输骨骼矩阵/常量缓冲区） |
| **缓存友好** | 差（需频繁更新 Vertex Buffer） | 优（Static Vertex Buffer） |
| **适用场景** | 移动端低端设备、需要 CPU 端碰撞检测、顶点数极少 | 通用 3D 游戏、复杂角色动画 |

### 数据存储：矩阵调色板 (Matrix Palette)
- **Constant Buffer (UBO)**：通常用于存储 `jointMatrices`。受限于 UBO 大小（如 64KB），通常限制单模型骨骼数（如 128 或 256 根）。
- **Texture / Buffer (TBO/SSBO)**：当骨骼数量巨大或需要做大量角色实例化 (Instancing) 时，将矩阵存在 Texture 或 Structured Buffer 中。

### 顶点属性压缩
- **Weights**：通常使用 `unorm8x4` 存储（4 字节），总和必须为 1.0。
- **Indices**：根据骨骼总数选择 `uint8x4` 或 `uint16x4`。

---

## 7. 调试与常见问题 (Troubleshooting)

### 1. 权重不归一化 (Normalization)
如果 $\sum Weight_i \neq 1.0$，模型在旋转时会发生整体缩放或位移异常。
- **解决**：在导出插件或 Shader 输入前强制归一化。

### 2. T-Pose vs. Bind Pose
- **Bind Pose** 是 Mesh 顶点定义的原始空间。
- 如果 IBM 矩阵与模型的 Bind Pose 不匹配，模型会出现爆炸式拉伸。

### 3. 最大影响骨骼数
glTF 标准通常支持 4 根（`JOINTS_0`, `WEIGHTS_0`），如果需要更多（如 8 根），需额外增加属性通道（`JOINTS_1`, `WEIGHTS_1`）。

### 4. 骨骼根节点偏移
如果 `GlobalTransform_Joint` 包含模型本身的 World Matrix，而 Shader 中又乘了一次 `modelMatrix`，会导致双重变换（模型飞走）。
- **解决**：确保矩阵链计算中，空间变换逻辑统一。

---

## 8. Shader 实现示例
  
### GLSL (glTF 风格)
```glsl
// 顶点属性
in vec3 position;
in vec4 jointWeights;  // WEIGHTS_0
in uvec4 jointIndices; // JOINTS_0

uniform mat4 jointMatrices[MAX_JOINTS]; 

void main() {
    mat4 skinMatrix = 
        jointWeights.x * jointMatrices[jointIndices.x] +
        jointWeights.y * jointMatrices[jointIndices.y] +
        jointWeights.z * jointMatrices[jointIndices.z] +
        jointWeights.w * jointMatrices[jointIndices.w];
        
    vec4 skinnedPosition = skinMatrix * vec4(position, 1.0);
    gl_Position = projectionMatrix * viewMatrix * modelMatrix * skinnedPosition;
}
```

### HLSL (D3D11 风格)
```hlsl
struct VS_INPUT {
    float3 Pos : POSITION;
    float4 Weights : BLENDWEIGHT;
    uint4  Indices : BLENDINDICES;
};

cbuffer SkinningData : register(b1) {
    float4x4 gBoneTransforms[96];
};

float4 main(VS_INPUT input) : SV_POSITION {
    float4x4 skinMatrix = 0;
    for(int i = 0; i < 4; i++) {
        skinMatrix += input.Weights[i] * gBoneTransforms[input.Indices[i]];
    }
    
    float4 worldPos = mul(float4(input.Pos, 1.0f), skinMatrix);
    return mul(worldPos, gViewProjection);
}
```
