
### Controller: [[Animation Controller]]

```csharp
public Animator animator;
private int moveChangeAni;

private void Awake() 
{
	animator = GetComponentInChildren<Animator>();
}
```




### enabled
动画将**立即停止播放**

```cpp
animator.enabled = false;
```