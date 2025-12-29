- 让玩家既能操作游戏（比如移动角色），又能使用鼠标与 UI 交互，同时让鼠标光标显示在屏幕上

```cpp
FInputModeGameAndUI InputMode;  
OwningController->SetInputMode(InputMode);  
OwningController->SetShowMouseCursor(true);
```


- 让玩家只进行游戏控制（如移动/攻击等），禁用 UI 控制，同时隐藏鼠标光标。 


```cpp
FInputModeGameOnly InputMode;  
OwningController->SetInputMode(InputMode);  
OwningController->SetShowMouseCursor(false);
```
