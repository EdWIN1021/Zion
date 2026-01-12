# RotationRate

Category: Property
Description: Change in rotation per second, used when UseControllerDesiredRotation or OrientRotationToMovement are true. Set a negative value for infinite rotation rate and instant turns.

```cpp
UPROPERTY(Category="Character Movement (Rotation Settings)", EditAnywhere, BlueprintReadWrite)
FRotator RotationRate;
```

```cpp
GetCharacterMovement()->RotationRate = FRotator(0.f, 400.f, 0.f);
```