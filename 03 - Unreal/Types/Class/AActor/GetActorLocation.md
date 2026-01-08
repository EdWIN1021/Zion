---
Class: "[[AActor]]"
Category: Function
Description: Returns the location of the RootComponent of this Actor
Return Type: "[[FVector]]"
---
## **Declaration**

```cpp
FORCEINLINE FVector GetActorLocation() const
{
	return TemplateGetActorLocation( ToRawPtr( RootComponent ) );
}
```

## **Example**

```cpp
FVector Location = GetActorLocation();
```
