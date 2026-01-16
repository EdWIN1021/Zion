[[Snippet.UE.TSoftClassPtr]]

- 它是一种不会立即加载资源、只在需要时才加载的智能引用，适合延迟加载类（比如蓝图类）
- `UClass*` / `TSubclassOf` 是 **强引用**，一旦使用，就会强制把资源加载进内存
- `TSoftClassPtr` 只是保存了一个 **路径 (asset path)**，不会立刻加载

## 优点
- 减少启动时间
    - 游戏启动时不会立刻加载所有引用的资源， 只有当用到的时候才加载，减少内存压力和加载卡顿
    
- 避免硬依赖
    - 如果你在一个核心类里直接 `UClass*` 指向某个大 UI 蓝图，那这个蓝图资源会被强制打进包里, 用 `TSoftClassPtr` 可以让资源独立存在，避免模块之间强耦合
    
- 和 AssetManager 配合  ([**Asynchronous Loading**](https://www.notion.so/Asynchronous-Loading-1ed8d590ff3880069166e8826de4bfe5?pvs=21) )
    - `TSoftClassPtr` 经常用在资源管理系统里，比如 AssetManager，可以在需要时才加载对应的类

## 适合用的场景
- UI 界面蓝图
- 大型关卡资源引用
- 角色职业类、怪物类（在游戏中根据配置才生成）