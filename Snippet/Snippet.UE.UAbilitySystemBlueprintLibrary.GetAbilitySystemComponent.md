# GetAbilitySystemComponent

Tags: static

```cpp
	UFUNCTION(BlueprintPure, Category = Ability, Meta=(DefaultToSelf = "Actor"))
	static UAbilitySystemComponent* GetAbilitySystemComponent(AActor* Actor);
```

```cpp
const UAbilitySystemComponent* SourceASC = UAbilitySystemBlueprintLibrary::GetAbilitySystemComponent(GetAvatarActorFromActorInfo());
```