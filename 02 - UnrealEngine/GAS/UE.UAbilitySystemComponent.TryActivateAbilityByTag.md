# TryActivateAbilityByTag

Description: Attempts to activate every gameplay ability that matches the given tag and DoesAbilitySatisfyTagRequirements()
Category: Function

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "Abilities")
bool TryActivateAbilitiesByTag(const FGameplayTagContainer& GameplayTagContainer, bool bAllowRemoteActivation = true);
```

## **Example**

```cpp
TargetASC->TryActivateAbilitiesByTag(TagContainer);
```