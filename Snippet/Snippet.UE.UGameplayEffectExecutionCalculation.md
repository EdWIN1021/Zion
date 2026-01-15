# UGameplayEffectExecutionCalculation

System: GAS
Type: Class

[UGameplayEffectExecutionCalculation](UGameplayEffectExecutionCalculation/UGameplayEffectExecutionCalculation%201798d590ff38807da658ee85278638e1.csv)

- No prediction
- Only Instant or Periodic Gameplay Effects
- Capturing doesn’t run `PreAttributeChange`; any clamping done there must be done again
- Only executed on the Server from Gameplay Abilities with local predicted, Server Initiated, and Server Only Net Execution Policies

![Screenshot 2025-01-09 203021.png](UGameplayEffectExecutionCalculation/Screenshot_2025-01-09_203021.png)

- Create Gameplay Effect Execution Calculation base on C++ Class
- Assign GEExecCalc to GE_Damage

![Screenshot 2025-01-09 203359.png](UGameplayEffectExecutionCalculation/Screenshot_2025-01-09_203359.png)

## **Execution Calculation Setup**

- **Attribute Capture Structure**
    
    ```cpp
    // Defines attribute capture rules for damage calculation
    struct FWarriorDamageCapture {
        DECLARE_ATTRIBUTE_CAPTUREDEF(AttackPower)  // Source attacker's offensive capability
        DECLARE_ATTRIBUTE_CAPTUREDEF(DefensePower) // Target defender's damage mitigation
    
        FWarriorDamageCapture() {
            // Configure source/target relationships
            DEFINE_ATTRIBUTE_CAPTUREDEF(UWarriorAttributeSet, AttackPower, Source, false);
            DEFINE_ATTRIBUTE_CAPTUREDEF(UWarriorAttributeSet, DefensePower, Target, false);
        }
    };
    ```
    

- **Singleton Access Pattern**
    
    ```cpp
    static const FWarriorDamageCapture& GetWarriorDamageCapture() {
        static FWarriorDamageCapture WarriorDamageCapture;
        return WarriorDamageCapture;
    }
    ```
    

- **Execution Class Initialization** in  Constructor
    
    ```cpp
     // Register captured attributes
     RelevantAttributesToCapture.Add(GetWarriorDamageCapture().AttackPowerDef);
     RelevantAttributesToCapture.Add(GetWarriorDamageCapture().DefensePowerDef);
    ```
    

- Override Execute function
    
    ```cpp
    virtual void Execute_Implementation(const FGameplayEffectCustomExecutionParameters& ExecutionParams, FGameplayEffectCustomExecutionOutput& OutExecutionOutput) const override;
    ```
    

## **Damage Calculation Logic**

```cpp
const FGameplayEffectSpec& EffectSpec = ExecutionParams.GetOwningSpec();
	
	
EffectSpec.GetContext().GetSourceObject();
EffectSpec.GetContext().GetAbility();
EffectSpec.GetContext().GetInstigator();
EffectSpec.GetContext().GetEffectCauser();
	
FAggregatorEvaluateParameters EvaluateParameters;

EvaluateParameters.SourceTags = EffectSpec.CapturedSourceTags.GetAggregatedTags();
EvaluateParameters.TargetTags = EffectSpec.CapturedTargetTags.GetAggregatedTags();
	
float SourceAttackPower = 0.f;
ExecutionParams.AttemptCalculateCapturedAttributeMagnitude(GetWarriorDamageCapture().AttackPowerDef, EvaluateParameters, SourceAttackPower);
	
float TargetDefensePower = 0.f;
ExecutionParams.AttemptCalculateCapturedAttributeMagnitude(GetWarriorDamageCapture().DefensePowerDef, EvaluateParameters, TargetDefensePower);
	
float BaseDamage = 0.f;
	
for (const TPair<FGameplayTag, float>& TagMagnitude : EffectSpec.SetByCallerTagMagnitudes)
{
		if (TagMagnitude.Key.MatchesTagExact(WarriorGameplayTags::Shared_SetByCaller_BaseDamage))
		{
			BaseDamage = TagMagnitude.Value;
		}
}
	
const float FinalDamageDone = BaseDamage * SourceAttackPower / TargetDefensePower;
	
			OutExecutionOutput.AddOutputModifier(
				FGameplayModifierEvaluatedData(
					GetWarriorDamageCapture().DamageTakenProperty,
					EGameplayModOp::Override,
					FinalDamageDone
				)
		);
	
```

## **Attribute Modification**

Override [`*PostGameplayEffectExecute*`](UAttributeSet/@UAttributeSet/PostGameplayEffectExecute%201898d590ff3880e2a59fdeddeed3064c.md) function in [`UAttributeSet`](UAttributeSet%201758d590ff3880819985e2eabfbbe876.md) 

**Post-Effect Execution**

```cpp
	if (Data.EvaluatedData.Attribute == GetDamageTakenAttribute())
	{
		const float OldHealth = GetCurrentHealth();
		const float DamageDone = GetDamageTaken();

		const float NewCurrentHealth = FMath::Clamp(OldHealth - DamageDone, 0.f, GetMaxHealth());
		SetCurrentHealth(NewCurrentHealth);
	}
```