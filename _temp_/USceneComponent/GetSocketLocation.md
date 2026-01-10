---
Class: "[[USceneComponent 1]]"
Category: Function
Description: Get world-space socket or bone location
Return Type: "[[Snippet.UE.Struct.FVector]]"
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
