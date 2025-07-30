## 使用 `TSubclassOf` 动态创建并管理 HUD Widget 实例

```cpp
/*  
 * 用于指定要生成哪种 Widget 类  
 * 因为 CreateWidget 是在运行时动态创建对象，而不是使用现成的对象，所以你必须传一个“类”（不是“对象”），用于 创建出新实例。  
 */
UPROPERTY(EditDefaultsOnly, Category = "Inventory")  
TSubclassOf<UInv_HUDWidget> HUDWidgetClass;  
  
/* 用于指向实际的 Widget 实例 */UPROPERTY()  
TObjectPtr<UInv_HUDWidget> HUDWidget;
```


```cpp
HUDWidget = CreateWidget<UInv_HUDWidget>(this, HUDWidgetClass);  
  
if (IsValid(HUDWidget))  
{  
    HUDWidget->AddToViewport();  
}
```

---

### Overlay
- Stacks widgets in layers, with each new widget layered on top of the previous one

### Canvas Panel
- 可以指定控件的:
	- X/Y 位置
	- Anchors（锚点）
	- Alignment（对齐方式）
	-  Size（宽高）

### Button
- Events
	- OnClicked

### Size Box
- 强制子控件使用特定的大小，而不是让子控件自由伸缩。

### Switcher




### Fill Screen
- 让 Widget UI 填满整个屏幕

### Draw As
- Image: 直接把整张图像按原样绘制，不进行拉伸切割处理

