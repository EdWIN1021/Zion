# SetReplicationMode

Tags: virtual
Description: When true, we will not replicate active gameplay effects for this ability system component, so attributes and tags
Category: Function

## **Declaration**

```cpp
virtual void SetReplicationMode(EGameplayEffectReplicationMode NewReplicationMode);
```

## **Example**

```cpp
// Mixed: Multiplayer

AbilitySystemComponent->SetReplicationMode(EGameplayEffectReplicationMode::Mixed);
```