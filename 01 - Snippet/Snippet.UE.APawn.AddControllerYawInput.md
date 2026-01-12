# AddControllerYawInput

Tags: virtual
Description: Add input (affecting Yaw) to the Controller's ControlRotation, if it is a local PlayerController

## **Declaration**

```cpp
	/**
	 * This value is multiplied by the PlayerController's InputYawScale value.
	 * @param Val Amount to add to Yaw. This value is multiplied by the PlayerController's InputYawScale value.
	 * @see PlayerController::InputYawScale
	 */
	UFUNCTION(BlueprintCallable, Category="Pawn|Input", meta=(Keywords="left right turn addyaw"))
	ENGINE_API virtual void AddControllerYawInput(float Val);
```

## **Example**

```cpp
AddControllerPitchInput(Value);
```