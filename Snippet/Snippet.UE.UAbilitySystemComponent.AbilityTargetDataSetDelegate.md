# AbilityTargetDataSetDelegate

Description: Returns TargetDataSet delegate for a given Ability/PredictionKey pair

## **Declaration**

```cpp
FAbilityTargetDataSetDelegate& AbilityTargetDataSetDelegate(FGameplayAbilitySpecHandle AbilityHandle, FPredictionKey AbilityOriginalPredictionKey);
```

## **Example**

```cpp
AbilitySystemComponent.Get()->AbilityTargetDataSetDelegate(SpecHandle, ActivationPredictionKey)
	.AddUObject(this, &UTargetDataUnderMouse::OnTargetDataReplicatedCallback);
```