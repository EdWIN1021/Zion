# AddLooseGameplayTag

Category: Function

**Loose Tags:** Temporary tags added/removed **at runtime**

## **Declaration**

```cpp
	FORCEINLINE void AddLooseGameplayTag(const FGameplayTag& GameplayTag, int32 Count=1)
	{
		UpdateTagMap(GameplayTag, Count);
	}
```

## **Example**

```cpp
ASC->AddLooseGameplayTag(TagToAdd);
```