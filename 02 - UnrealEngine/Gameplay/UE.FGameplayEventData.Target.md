# Target

Description: The target of the event

## **Declaration**

```cpp
UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = GameplayAbilityTriggerPayload)
TObjectPtr<const AActor> Target;
```

## **Example**

```cpp
Data.Target = HitActor;
```