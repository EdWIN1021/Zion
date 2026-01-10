---
Class: "[[_temp_/Unreal/Types/Class/AActor/AActor]]"
Category: Function
Description: Returns the location of the RootComponent of this Actor
Return Type: "[[Snippet.UE.Struct.FVector]]"
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
