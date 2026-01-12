# MaxWalkSpeed

Category: Property
Description: The maximum ground speed when walking. Also determines maximum lateral speed when falling.

```cpp
UPROPERTY(Category="Character Movement: Walking", EditAnywhere, BlueprintReadWrite, meta=(ClampMin="0", UIMin="0", ForceUnits="cm/s"))
float MaxWalkSpeed;
```

```cpp
GetCharacterMovement()->MaxWalkSpeed = 400.f;
```