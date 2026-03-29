# SetSetByCallerMagnitude

Access Specifier: Public
Category: Function
Description: Sets the magnitude of a SetByCaller modifier

## **Declaration**

```cpp
void SetSetByCallerMagnitude(FGameplayTag DataTag, float Magnitude);
```

## **Example**

```cpp
EffectSpecHandle.Data->SetSetByCallerMagnitude(WarriorGameplayTags::Shared_SetByCaller_BaseDamage, InWeaponBaseDamage);
```