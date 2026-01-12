# GetActorNameOrLabel

Category: Function

## **Declaration**

```cpp
	const FString GetActorNameOrLabel() const
	{
#if WITH_EDITORONLY_DATA || (!WITH_EDITOR && ACTOR_HAS_LABELS)
		if (!ActorLabel.IsEmpty())
		{
			return ActorLabel;
		}
#endif
		return GetName();
	}
```

## **Example**

```cpp

```