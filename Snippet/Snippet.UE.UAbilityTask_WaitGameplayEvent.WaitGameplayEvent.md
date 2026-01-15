# WaitGameplayEvent

Access Specifier: public
Tags: BlueprintCallable
Description: Wait until the specified gameplay tag event is triggered.

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "Ability|Tasks", meta = (HidePin = "OwningAbility", DefaultToSelf = "OwningAbility", BlueprintInternalUseOnly = "TRUE"))
static UAbilityTask_WaitGameplayEvent* WaitGameplayEvent(UGameplayAbility* OwningAbility, FGameplayTag EventTag, AActor* OptionalExternalTarget=nullptr, bool OnlyTriggerOnce=false, bool OnlyMatchExact = true);
```

## **Example**

```cpp

```