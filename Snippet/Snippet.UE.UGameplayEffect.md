# UGameplayEffect

Base: UObject (UObject%201378d590ff3880b19696d9852e8a88d8.md) 
System: GAS
Type: Class

<aside>

[UObject](UObject%201378d590ff3880b19696d9852e8a88d8.md) → [UGameplayEffect](UGameplayEffect%201758d590ff3880afbbabe45476a16c64.md) 

</aside>

[@UGameplayEffect ](UGameplayEffect/@UGameplayEffect%201758d590ff3880c7ad08dc50220ad90e.csv)

- This method retrieves the default object for the class.

```cpp
for(const TSubclassOf<UGameplayEffect>& EffectClass : StartUpGameplayEffects) { 
		if(!EffectClass) continue; 
		UGameplayEffect* EffectCDO = EffectClass->GetDefaultObject<UGameplayEffect>(); 
		InASCToGive->ApplyGameplayEffectToSelf(EffectCDO, ApplyLevel, InASCToGive->MakeEffectContext()); 
}
```

- Dynamic Gameplay Effects

```cpp
UGameplayEffect* Effect = NewObject<UGameplayEffect>(GetTransientPackage(), FName(DebuffName));
```

1. **Declare the Effect Class**
    
    ```cpp
    cpp
    CopyEdit
    // In your Ability’s header:
    UPROPERTY(EditDefaultsOnly, Category = “GameplayEffect”)
    TSubclassOf<UGameplayEffect> DamageEffectClass;
    ```
    
    - Expose it in the editor so you can assign your `GE_Damage` blueprint
2. **Make the Effect Context**
    
    ```cpp
    // Build the context for who caused this effect
    FGameplayEffectContextHandle ContextHandle = GetWarriorAbilitySystemComponentFromActorInfo()->MakeEffectContext();
    ContextHandle.SetAbility(this);
    ContextHandle.AddSourceObject(GetAvatarActorFromActorInfo());
    ContextHandle.AddInstigator(GetAvatarActorFromActorInfo(), GetAvatarActorFromActorInfo());
    ```
    
    - **SetAbility(this)** ties the effect back to this UGameplayAbility
    - **AddSourceObject** & **AddInstigator** mark the actor that “owns” and “instigates” the damage
3. **Create the Spec Handle**
    
    ```cpp
    // Level is usually the ability’s current level
    const int32 AbilityLevel = GetAbilityLevel();
    
    FGameplayEffectSpecHandle SpecHandle = GetWarriorAbilitySystemComponentFromActorInfo()->MakeOutgoingSpec(
                DamageEffectClass,
                AbilityLevel,
                ContextHandle
    );
    ```
    
    - `MakeOutgoingSpec()` packages the class, level, and context into a “spec” you can tweak
4. **Set Dynamic Magnitude (SetByCaller)**
    
    ```cpp
    // Using your custom tag for base damage
    static const FGameplayTag Tag_BaseDamage = WarriorGameplayTags::Shared_SetByCaller_BaseDamage;
    
    // Pass in the weapon’s base damage at runtime
    SpecHandle.Data->SetSetByCallerMagnitude(Tag_BaseDamage, InWeaponBaseDamage);
    ```
    
    - **SetByCaller** lets you vary damage without creating dozens of effect assets
5. **Apply the Spec to a Target**
    
    ```cpp
    // Assuming you have a valid target ASC
    UAbilitySystemComponent* TargetASC = /* … */;
    TargetASC->ApplyGameplayEffectSpecToSelf(*SpecHandle.Data.Get());
    ```
    
    - You can also use `ApplyGameplayEffectSpecToTarget()` if you want to specify the target actor explicitly
6. [`UGameplayEffectExecutionCalculation`](UGameplayEffectExecutionCalculation%201778d590ff38808c958be6f9eb364860.md)