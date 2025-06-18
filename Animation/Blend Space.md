#### Smoothing Time

假设你有一个 1D BlendSpace 控制“角色速度”的动画：

- 输入值 `0`：站立动画
- 输入值 `300`：走路动画
- 输入值 `600`：跑步动画
    
当你把速度从 0 改成 600：

- 没有 Smoothing Time → 会立刻切换到跑步（非常生硬）
- 有 Smoothing Time = 0.2 秒 → 会在 0.2 秒内从站立平滑过渡到跑步

#### Smoothing Type

**Cubic smoothing（立方平滑）** 是一种基于三次函数的插值方式。  

它的变化趋势通常是：

- **开始较慢 → 中间加速 → 结束再减速**
- 给人一种“自然加速和减速”的感觉
- 类似 easing 曲线里的 **ease-in-out** 效果