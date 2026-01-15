# FScopedAbilityListLock

Type: Struct

<aside>

- **Safely access or modify the ability list** in the `AbilitySystemComponent`
- **Thread Safety**: Locks the ability list to prevent race conditions during multi-threaded operations.
- Used to stop us from removing abilities from an ability system component while we're iterating through the abilities
</aside>

```cpp
FScopedAbilityListLock ActiveScopeLock(*this);
```