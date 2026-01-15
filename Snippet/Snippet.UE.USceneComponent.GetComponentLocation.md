# GetComponentLocation

Access Specifier: public
Tags: funciton
Description: Return location of the component, in world space

```cpp
	FORCEINLINE FVector GetComponentLocation() const
	{
		return GetComponentTransform().GetLocation();
	}
```