## IA_Move

![[Screenshot 2025-12-29 125648.png | center]]


### Create the Callback Functions

- MoveForward Function

```cpp
void ABird::MoveForward(float Value){
	if(!Controller && (value != 0.f))
	{
		const FRotator ControlRotation = GetControlRotation();
		const FRotator YawRotation(0.f, ControlRotation.Yaw, 0.f);

		// Construct a rotation matrix from the yaw rotation,
		// then extract the X axis (forward direction) as a unit vector.
		const FVector Direction = FRotationMatrix(YawRotation).GetUnitAxis(EAxis::X);
		AddMovementInput(Direction, Value);
	}
}
```

- MoveRight Function

```cpp
void ASlashCharacter::MoveRight(float Value)
{
	if (Controller && Value != 0.f)
	{
		const FRotator ControlRotation = GetControlRotation();
		const FRotator YawRotation(0.f, ControlRotation.Yaw, 0.f);
		const FVector Direction = FRotationMatrix(YawRotation).GetUnitAxis(EAxis::Y);
		AddMovementInput(Direction, Value);
	}
}
```

- Turn Function

```cpp
void ABird::Turn(float Value){
	AddControllerYawInput(Value);
}
```

- LookUp Function

```cpp
void Abird::LookUp(float Value){
	AddControllerPitchInput(Value);
}
```

- Jump
    
- Add a [`UFloatingPawnMovement`](https://www.notion.so/UFloatingPawnMovement-1d08d590ff3880cea074f1f9618ef40a?pvs=21) component to BP
    
### **Bind the Axis in the Input Component**

```cpp
void ABird::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent){
    Super::SetupPlayerInputComponent(PlayerInputComponent);
    
    PlayerInputComponent->BindAxis(FName("MoveForward"), this, &ASlashCharacter::MoveForward);
	PlayerInputComponent->BindAxis(FName("MoveRight"), this, &ASlashCharacter::MoveRight);
	PlayerInputComponent->BindAxis(FName("Turn"), this, &ASlashCharacter::Turn);
	PlayerInputComponent->BindAxis(FName("LookUp"), this, &ASlashCharacter::LookUp);
		
	PlayerInputComponent->BindAction(FName("Jump"), IE_Pressed, this, &ACharacter::Jump);
	PlayerInputComponent->BindAction(FName("Equip"), IE_Pressed, this, &ASlashCharacter::EKeyPressed);
}
```

### Additional Movement and Camera Settings

```cpp
bUseControllerRotationRoll = false;
bUseControllerRotationPitch = false;
bUseControllerRotationYaw = false;
GetCharacterMovement()->bOrientRotationToMovement = true;
GetCharacterMovement()->RotationRate = FRotator(0.f, 400.f, 0.f);
```

### [Camera and Spring Arm](https://www.notion.so/Camera-and-Spring-Arm-1d08d590ff388095bb83e80715a86022?pvs=21)

<aside>

Camera Boom

- Camera Settings
    - [`bUsePawnControlRotation`](https://www.notion.so/bUsePawnControlRotation-18c8d590ff388016aac6e06b16fc4a4a?pvs=21) → true </aside>