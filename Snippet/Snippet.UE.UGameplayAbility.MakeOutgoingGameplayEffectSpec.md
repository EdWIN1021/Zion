# MakeOutgoingGameplayEffectSpec

Tags: BlueprintCallable
Category: Function

```cpp
UFUNCTION(BlueprintCallable, Category=Ability)
FGameplayEffectSpecHandle MakeOutgoingGameplayEffectSpec(TSubclassOf<UGameplayEffect> GameplayEffectClass, float Level=1.f) const;
```

```cpp
const FGameplayEffectSpecHandle DamageSpecHandle = MakeOutgoingGameplayEffectSpec(DamageEffectClass, 1);
```