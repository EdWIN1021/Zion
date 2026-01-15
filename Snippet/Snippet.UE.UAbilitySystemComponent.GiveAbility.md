# GiveAbility

Category: Function
Return: FGameplayAbilitySpecHandle (../../FGameplayAbilitySpecHandle%201978d590ff3880dabc2cdc5958c8f327.md)

<aside>

- Grant abilities to an actor
- **Server Authority**: In multiplayer, call `GiveAbility` on the **server**; the ASC replicates granted abilities to clients.
- 
</aside>

## **Declaration**

```cpp
FGameplayAbilitySpecHandle GiveAbility(const FGameplayAbilitySpec& AbilitySpec);
```

## **Example**

```cpp
GiveAbility(AbilitySpec);
```