# AbilitySpecInputReleased

Description: Called on local player always. Called on server only if bReplicateInputDirectly is set on the GameplayAbility

## **Declaration**

```cpp
virtual void AbilitySpecInputReleased(FGameplayAbilitySpec& Spec);
```

## **Example**

```cpp
AbilitySpecInputReleased(AbilitySpec);
```