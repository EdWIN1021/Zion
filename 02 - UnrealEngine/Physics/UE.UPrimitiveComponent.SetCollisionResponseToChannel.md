# SetCollisionResponseToChannel

Access Specifier: public
Description: Changes a member of the ResponseToChannels container for this PrimitiveComponent

## **Declaration**

```cpp
/**
	*
	* @param       Channel      The channel to change the response of
	* @param       NewResponse  What the new response should be to the supplied Channel
	*/
UFUNCTION(BlueprintCallable, Category="Collision")
ENGINE_API virtual void SetCollisionResponseToChannel(ECollisionChannel Channel, ECollisionResponse NewResponse);
	
```

## **Example**

```cpp
GeometryCollection->SetCollisionResponseToChannel(ECC_Camera, ECR_Ignore);
GetMesh()->SetCollisionResponseToChannel(ECC_WorldStatic, ECR_Block);
```