# SetIsReplicated

Description: Enable or disable replication. This is the equivalent of RemoteRole for actors (only a bool is required for components)
Category: Function

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Components")
ENGINE_API void SetIsReplicated(bool ShouldReplicate);
```

## **Example**

```cpp
AbilitySystemComponent->SetIsReplicated(true);
```