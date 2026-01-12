# GetControlRotation

Access Specifier: public
Category: Function
Description: Get the control rotation

## **Declaration**

```cpp
/**
	* This is the full aim rotation, which may be different than a camera orientation (for example in a third person view),
	* and may differ from the rotation of the controlled Pawn (which may choose not to visually pitch or roll, for example).
	*/
UFUNCTION(BlueprintCallable, Category=Pawn)
ENGINE_API virtual FRotator GetControlRotation() const;
```

## **Example**

```cpp
const FRotator Rotation = GetControlRotation();
```