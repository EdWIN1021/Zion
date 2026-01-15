# AddMovementInput

Tags: virtual
Description: Add movement input along the given world direction vector

## **Declaration**

```cpp
/**
	* Add movement input along the given world direction vector (usually normalized) scaled by 'ScaleValue'. If ScaleValue < 0, movement will be in the opposite direction.
	* Base Pawn classes won't automatically apply movement, it's up to the user to do so in a Tick event. Subclasses such as Character and DefaultPawn automatically handle this input and move.
	*
	* @param WorldDirection	Direction in world space to apply input
	* @param ScaleValue		Scale to apply to input. This can be used for analog input, ie a value of 0.5 applies half the normal value, while -1.0 would reverse the direction.
	* @param bForce			If true always add the input, ignoring the result of IsMoveInputIgnored().
	* @see GetPendingMovementInputVector(), GetLastMovementInputVector(), ConsumeMovementInputVector()
	*/
UFUNCTION(BlueprintCallable, Category="Pawn|Input", meta=(Keywords="AddInput"))
ENGINE_API virtual void AddMovementInput(FVector WorldDirection, float ScaleValue = 1.0f, bool bForce = false);

```

## **Example**

```cpp
void ABird::MoveForward(float Value){
	if(!Controller && (value != 0.f))
	{
			FVector Forward = GetActorForwardVector();
			AddMovementInput(Forward, Value);
	}
}
```