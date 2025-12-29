---
Category: Function
---
```cpp
UFUNCTION(BlueprintCallable, Category="Actor")  
ENGINE_API bool ActorHasTag(FName Tag) const;
```

```cpp
const FName TargetTag = OwningPawn->ActorHasTag(FName("Player")) ? FName("Enemy"): FName("Player");
```

