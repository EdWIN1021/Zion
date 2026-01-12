# MarkAbilitySpecDirty

Category: Function

<aside>

- Call to mark that an ability spec has been modified
- Notifies the engine that a specific `FGameplayAbilitySpec` has been modified and needs to be replicated to clients.
</aside>

## **Declaration**

```cpp
	void MarkAbilitySpecDirty(FGameplayAbilitySpec& Spec, bool WasAddOrRemove=false);
```

## **Example**

```cpp
MarkAbilitySpecDirty(AbilitySpec);
```