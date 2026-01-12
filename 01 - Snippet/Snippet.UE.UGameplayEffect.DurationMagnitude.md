# DurationMagnitude

Access Specifier: public
Category: Property
Type: FGameplayEffectModifierMagnitude (../../FGameplayEffectModifierMagnitude%201a38d590ff388048a423c5b1a63a20fa.md)

<aside>

Duration in seconds. 0.0 for instantaneous effects; -1.0 for infinite duration.

</aside>

```cpp
UPROPERTY(EditDefaultsOnly, Category=Duration, meta=(EditCondition="DurationPolicy == EGameplayEffectDurationType::HasDuration", EditConditionHides))
FGameplayEffectModifierMagnitude DurationMagnitude;
```