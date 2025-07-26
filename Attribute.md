
### Header
用于在 **Inspector（检视器）** 中为字段分组加上标题，提升可读性和组织性

```cpp
[Header("Movement details")] 
public float idleTime = 2;  
public float moveSpeed = 1.4f;
```

### Range

快速限制一个变量的值范围

```cpp
[Range(0, 2)]  // 其值只能在 0 到 2 之间调整
public float moveAnimSpeedMultiplier = 1;
```



### Space
用来在 **Inspector 面板中添加垂直间距**，让变量之间看起来更整洁、分组更清晰

```cpp
[Space]
```


### ContextMenu
用于将一个方法添加到 Unity 编辑器中组件的右键上下文菜单中

```cpp
[ContextMenu("Stun Enemy")]
public void HandleCounter()  
{  
	stateMachine.ChangeState(stunnedState);  
}
```
