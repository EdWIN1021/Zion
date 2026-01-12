# Instigator

Description: The instigator of the event

## **Declaration**

```cpp
PROPERTY(EditAnywhere, BlueprintReadWrite, Category = GameplayAbilityTriggerPayload)
TObjectPtr<const AActor> Instigator;
```

## **Example**

```cpp
Data.Instigator = GetOwningPawn();
```