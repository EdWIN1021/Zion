---
Class: "[[_temp_/Unreal/Types/Class/USceneComponent/USceneComponent]]"
Category: Function
Description: Get world-space socket or bone location
Return Type: "[[FVector]]"
---
## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Transformation", meta=(Keywords="Bone")) 
ENGINE_API virtual FVector GetSocketLocation(FName InSocketName) const;
```

## **Example**

```cpp
Weapon->GetSocketLocation(WeaponTipSocketName)
```
