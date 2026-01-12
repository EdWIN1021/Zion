# AddControllerPitchInput

Tags: virtual
Description: Add input (affecting Pitch) to the Controller's ControlRotation, if it is a local PlayerController

## **Declaration**

```cpp
/**
	* This value is multiplied by the PlayerController's InputPitchScale value.
	* @param Val Amount to add to Pitch. This value is multiplied by the PlayerController's InputPitchScale value.
	* @see PlayerController::InputPitchScale
	*/
UFUNCTION(BlueprintCallable, Category="Pawn|Input", meta=(Keywords="up down addpitch"))
ENGINE_API virtual void AddControllerPitchInput(float Val);
```

## **Example**

```cpp
AddControllerPitchInput(Value);
```