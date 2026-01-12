# bOrientRotationToMovement

Category: Property
Description: When bOrientRotationToMovement is set to true, the character will rotate its orientation (view or body) to face the direction it is moving. This makes movements appear more natural and responsive.

```cpp
UPROPERTY(Category="Character Movement (Rotation Settings)", EditAnywhere, BlueprintReadWrite)
	uint8 bOrientRotationToMovement:1;
```

```cpp
	GetCharacterMovement()->bOrientRotationToMovement = true;
```