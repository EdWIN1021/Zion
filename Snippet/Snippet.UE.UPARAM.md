# UPARAM

Type: Macro

## ref

```cpp
/* In Blueprint‐exposed C++ this macro marks the array as passed by reference (so Blueprint pins will modify the caller’s variable) */
void RemoveGrantHeroWeaponAbilities(UPARAM(ref) TArray<FGameplayAbilitySpecHandle>& InSpecHandlesToRemove);
```

## Categories

```cpp
/* The list will only show tags that belong to the `Frontend.WidgetStack` category (defined in your project's settings) */
void RegisterWidgetStack(UPARAM(meta = (Categories = "Frontend.WidgetStack")) FGameplayTag InStackTag, UCommonActivatableWidgetContainerBase* InStack);
```