# AssignTagSetByCallerMagnitude

Tags: static

<aside>

- **`AssignTagSetByCallerMagnitude`** in Unreal Engine's Gameplay Ability System (GAS) is a method used to dynamically assign numerical values (magnitudes) to a Gameplay Effect using **Gameplay Tags** provided by the ability ("caller").
</aside>

```cpp
UFUNCTION(BlueprintCallable, Category = "Ability|GameplayEffect", meta = (GameplayTagFilter = "SetByCaller"))
static FGameplayEffectSpecHandle AssignTagSetByCallerMagnitude(FGameplayEffectSpecHandle SpecHandle, FGameplayTag DataTag, float Magnitude);
```

```cpp
UAbilitySystemBlueprintLibrary::AssignTagSetByCallerMagnitude(SpecHandle, DamageType, ScaledDamage);
```