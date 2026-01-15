# MakeEffectContext

Description: Create an EffectContext for the owner of this AbilitySystemComponent
Category: Function
Return: FGameplayEffectContextHandle  (../../FGameplayEffectContextHandle%2013f8d590ff3880c7a685ece8bd4bd01b.md)

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = GameplayEffects)
virtual FGameplayEffectContextHandle MakeEffectContext() const;
```

## **Example**

```cpp
FGameplayEffectContextHandle PrimaryAttributesContextHandle = ASC->MakeEffectContext();
```