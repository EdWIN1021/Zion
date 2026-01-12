# RequestGameplayTag

Category: Fucntion
Tags: Static

<aside>

- provides a hierarchical way to categorize and reference gameplay-related tags
</aside>

## Declaration

```cpp
	static GAMEPLAYTAGS_API FGameplayTag RequestGameplayTag(const FName& TagName, bool ErrorIfNotFound=true);
```

## Example

```cpp
FGameplayTag::RequestGameplayTag(FName("Abilities.Status")))
```