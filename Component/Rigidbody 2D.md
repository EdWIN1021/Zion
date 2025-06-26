#### Body Type
- Dynamic: Fully simulated by physics. Responds to **forces, gravity, collisions, and joints**.
- Kinematic: **Not affected by physics forces/gravity**. Movement is controlled **manually via scripts**.
- Static: **Immobile** and **ignores all physics**. Only used for collision detection.

#### Material
- This is a _shared physics material_ that overrides individual collider materials for simplicity 
- Physical Material 2D

#### Gravity Scale

#### Linear Damping
- **Linear Damping** (also called **Drag**) is a property of the `Rigidbody2D` component that **slows down linear movement** (translation) over time. It simulates resistance like air/fluid friction or drag forces, preventing objects from moving indefinitely.

#### Collision Detection
- Continuous: Continuous collision detection checks for collisions at every point in time as objects move
- Discrete: Discrete collision detection checks for collisions at specific intervals or frames rather than continuously. 

#### Interpolation
- _Interpolation_: 基于物体**过去几帧的位置数据**，在物理更新间隔之间插入中间位置，使运动看起来更平滑 (物体运动平稳、速度变化不剧烈时)
- _Extrapolation_: 基于物体**当前速度和方向**，预测其在**下一帧的位置**，提前生成平滑路径 (玩家角色、高速子弹等需要即时响应的物体)

#### Freeze Rotation Z


