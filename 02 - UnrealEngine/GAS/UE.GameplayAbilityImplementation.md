### 1. **Create a New C++ Class for the Custom Ability**

- Open your Unreal Engine project.
- Navigate to `Content/Code` or your preferred folder structure.
- Right-click and select ** Class** -> **GameplayAbility**.
- Name your new class `UWarriorGameplayAbility`.
- Ensure it inherits from `UGameplayAbility`.

### 2. **Override the OnGiveAbility Function**

- In your `UWarriorGameplayAbility` class, override the `OnGiveAbility` function.
- This function is called when the ability is granted to an actor.

```cpp
void UWarriorGameplayAbility::OnGiveAbility(const FGameplayAbilityActorInfo* ActorInfo, const FGameplayAbilitySpec& Spec)
{
    Super::OnGiveAbility(ActorInfo, Spec);

    if (ActorInfo && !Spec.IsActive())
    {
        // Automatically activate the ability when it's given
        ActorInfo->AbilitySystemComponent->TryActivateAbility(Spec.Handle);
    }
}
```

### 3. **Override the EndAbility Function**

- Override the `EndAbility` function to handle any cleanup or additional logic when the ability ends.

```cpp
void UWarriorGameplayAbility::EndAbility(const FGameplayAbilitySpecHandle Handle, const FGameplayAbilityActorInfo* ActorInfo, const FGameplayAbilityActivationInfo ActivationInfo, bool bReplicateEndAbility, bool bWasCancelled)
{
    Super::EndAbility(Handle, ActorInfo, ActivationInfo, bReplicateEndAbility, bWasCancelled);

    if (ActorInfo)
    {
        // Clear the ability from the AbilitySystemComponent
        ActorInfo->AbilitySystemComponent->ClearAbility(Handle);
    }
}
```

### 4. **Create a Blueprint Class for Designer Use**

- Create a new blueprint class that inherits from your `UWarriorGameplayAbility`.
- Name it `BP_WarriorGameplayAbility`.
- This allows designers to use and modify the ability without writing code.