# TryActivateAbility

Category: Function

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "Abilities") 
bool TryActivateAbility(
	FGameplayAbilitySpecHandle AbilityToActivate, 
	bool bAllowRemoteActivation = true
);
```

## **Example**

```cpp
TryActivateAbility(AbilitySpec.Handle);
```