
`CalculateDirection()` calculates an angle based on the **movement direction** and the **facing direction** of the character.


```cpp title:CalculateDirection
float LocomotionDirection;

void UWarriorCharacterAnimInstance::NativeThreadSafeUpdateAnimation(float DeltaSeconds)  
{  
    LocomotionDirection = UKismetAnimationLibrary::CalculateDirection(OwningCharacter->GetVelocity(), OwningCharacter->GetActorRotation());  
}
```

| Moving straight forward | `0°`    |
| ----------------------- | ------- |
| Strafing right          | `+90°`  |
| Strafing left           | `-90°`  |
| Moving backward         | `±180°` |
