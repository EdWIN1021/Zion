# DurationMagnitude
- Duration in seconds. 0.0 for instantaneous effects; -1.0 for infinite duration.

```cpp
UPROPERTY(EditDefaultsOnly, Category=Duration, meta=(EditCondition="DurationPolicy == EGameplayEffectDurationType::HasDuration", EditConditionHides))
FGameplayEffectModifierMagnitude DurationMagnitude;
```
