# GetCharacterMovement

Access Specifier: public
Description: Returns CharacterMovement subobject
Return: UCharacterMovementComponent (../../UCharacterMovementComponent%2018d8d590ff3880e39efaf1783fc28990.md) 
Tags: funciton

## **Declaration**

```cpp
FORCEINLINE UCharacterMovementComponent* GetCharacterMovement() const { return CharacterMovement; }
```

## **Example**

```cpp
OwningMovementComponent = OwningCharacter->GetCharacterMovement();
```