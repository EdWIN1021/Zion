---
Class: "[[_temp_/Unreal/Types/Class/AActor/AActor]]"
Category: Function
Description:
Return Type:
---
## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Transformation") 
ENGINE_API virtual FVector GetVelocity() const;
```

## **Example**

```cpp
GroundSpeed = OwningCharacter->GetVelocity().Size2D();
```
