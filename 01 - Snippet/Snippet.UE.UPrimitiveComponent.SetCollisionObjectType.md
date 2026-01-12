# SetCollisionObjectType

Access Specifier: public
Description: Changes the collision channel that this object uses when it moves

## **Declaration**

```cpp
/**
	*	@param      Channel     The new channel for this component to use
	*/
UFUNCTION(BlueprintCallable, Category="Collision")	
ENGINE_API virtual void SetCollisionObjectType(ECollisionChannel Channel);
```

## **Example**

```cpp
	GetMesh()->SetCollisionObjectType(ECC_WorldDynamic);
```