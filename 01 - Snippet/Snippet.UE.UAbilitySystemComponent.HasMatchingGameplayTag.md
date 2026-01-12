# HasMatchingGameplayTag

Category: Function

## **Declaration**

```cpp
	FORCEINLINE bool HasMatchingGameplayTag(FGameplayTag TagToCheck) const override
	{
		return GameplayTagCountContainer.HasMatchingGameplayTag(TagToCheck);
	}
```

## **Example**

```cpp
	if(!ASC->HasMatchingGameplayTag(TagToAdd))
	{
		ASC->AddLooseGameplayTag(TagToAdd);
	}
```