# SetCollisionResponseToAllChannels

Access Specifier: public
Description: Changes all ResponseToChannels container for this PrimitiveComponent. to be NewResponse

## **Declaration**

```cpp
/**
	*
	* @param       NewResponse  What the new response should be to the supplied Channel
	*/
UFUNCTION(BlueprintCallable, Category="Collision")
ENGINE_API virtual void SetCollisionResponseToAllChannels(ECollisionResponse NewResponse);
```

## **Example**

```cpp
Sphere->SetCollisionResponseToAllChannels(ECR_Ignore);
```