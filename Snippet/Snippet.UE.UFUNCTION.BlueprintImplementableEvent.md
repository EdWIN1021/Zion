 **这个 C++ 函数可以在 Blueprint（蓝图）中被“实现”**，但它在 C++ 代码中**不需要定义（实现）**
## Function Declaration

```cpp
// BlueprintImplementableEvent -> dont need to make virtual
UFUNCTION(BlueprintImplementableEvent)
 void CreateFields(const FVector& FieldLocation);
```


## Call the Blueprint-implemented event
```cpp
CreateFields(BoxHit.ImpactPoint);
```


