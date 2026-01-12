# MakeOutgoingSpec (对外）

Description: Get an outgoing GameplayEffectSpec that is ready to be applied to other things.
Category: Function
Return: FGameplayEffectSpecHandle (../../FGameplayEffectSpecHandle%201778d590ff3880f9a90fc8327660a65b.md)

## **Declaration**

```cpp
	UFUNCTION(BlueprintCallable, Category = GameplayEffects)
	virtual FGameplayEffectSpecHandle MakeOutgoingSpec(TSubclassOf<UGameplayEffect> GameplayEffectClass, float Level, FGameplayEffectContextHandle Context) const;
```

## **Example**

```cpp
FGameplayEffectSpecHandle EffectSpecHandle = GetWarriorAbilitySystemComponentFromActorInfo()->MakeOutgoingSpec(EffectClass, GetAbilityLevel(), ContextHandle);
```