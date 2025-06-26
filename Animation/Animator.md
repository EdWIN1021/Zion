
#### Transitions
- Has Exit Time: false
	- Exit Time (如果你设置 `Exit Time = 0.75`，意味着：当前 `Attack` 动画播放到 75% 时，就允许跳转到 `Idle` 动画（如果条件满足）)
	- Transition Duration: 0

```csharp
public Animator animator;
private int moveChangeAni;


private void Awake() 
{
	animator = GetComponentInChildren<Animator>();
}
```