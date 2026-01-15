# How to create GameplayModMagnitudeCalculation

Tags: GAS

## Create a MMC base on [Gameplay Mod Magnitude Calculation](https://www.notion.so/UGameplayModMagnitudeCalculation-18f8d590ff3880588f3bcbf7d3b0993c?pvs=21)

## Generate Constructor

```cpp
	UMMC_MaxHealth();
```

## Override [`CalculateBaseMagnitude`](https://www.notion.so/CalculateBaseMagnitude-1928d590ff3880099a1af80300148076?pvs=21) Function

## Create a [`FGameplayEffectAttributeCaptureDefinition`](https://www.notion.so/FGameplayEffectAttributeCaptureDefinition-1928d590ff3880e98691e2f6c729e800?pvs=21) variable

```cpp
FGameplayEffectAttributeCaptureDefinition VigorDef;
```

## Setting the Attribute to Capture

```cpp
VigorDef.AttributeToCapture = UAuraAttributeSet::GetVigorAttribute();
```

Defining the Attribute Source

```cpp
VigorDef.AttributeSource = EGameplayEffectAttributeCaptureSource::Target;
```

Determining Snapshot Behavior

```cpp

VigorDef.bSnapshot = false;
```

Adding the Capture Definition to the List

```cpp
RelevantAttributesToCapture.Add(VigorDef);
```

Create `*FAggregatorEvaluateParameters*`

```cpp
	FAggregatorEvaluateParameters EvaluateParameters;
	EvaluateParameters.SourceTags = SourceTags;
	EvaluateParameters.TargetTags = TargetTags;
```

Call `*GetCapturedAttributeMagnitude*`

```cpp
	float Vigor = 0.f;
	GetCapturedAttributeMagnitude(VigorDef, Spec, EvaluateParameters, Vigor);
	Vigor = FMath::Max<float>(Vigor, 0.f);
```

## Gameplay Effect Blueprint

- Modifier Op - Override
- Magnitude Calculation Type - Custom Calculation Class
- Calculation Class - MMC