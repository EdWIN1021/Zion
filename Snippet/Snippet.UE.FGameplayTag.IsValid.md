# IsValid

Category: Fucntion
Description: Returns whether the tag is valid or not; Invalid tags are set to NAME_None and do not exist in the game-specific global dictionary

## **Declaration**

```cpp
FORCEINLINE bool IsValid() const
	{
		return (TagName != NAME_None);
	}
```

## **Example**

```cpp
InCurrentAttackTypeTag.IsValid()；
```