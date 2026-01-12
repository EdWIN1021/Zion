# GetActivatableAbilities

Description: Returns the list of all activatable abilities.
Category: Function

## **Declaration**

```cpp
const TArray<FGameplayAbilitySpec>& GetActivatableAbilities() const { return ActivatableAbilities.Items; }
```

## **Example**

```cpp
	for(const FGameplayAbilitySpec& AbilitySpec: GetActivatableAbilities())
	{
		if(!AbilitySpec.DynamicAbilityTags.HasTagExact(InInputTag)) continue;
		TryActivateAbility(AbilitySpec.Handle); 
	}
```