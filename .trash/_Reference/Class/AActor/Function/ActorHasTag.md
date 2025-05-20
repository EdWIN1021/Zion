---
Category: Function
Return: 
tags:
---



## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Actor")  
ENGINE_API bool ActorHasTag(FName Tag) const;
```

## **Example**

```cpp
const FName TargetTag = OwningPawn->ActorHasTag(FName("Player")) ? FName("Enemy"): FName("Player");
```