# SendGameplayEventToActor

Tags: BlueprintCallable
Description: This function can be used to trigger an ability on the actor in question with useful payload data
Files & media: ../Screenshot_2025-01-09_173337.png

*Trigger ability-driven logic through event tagging and payload data*

## **Function Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "Ability", Meta = (Tooltip = "Triggers an ability on the target actor using a gameplay tag and payload data."))
static void SendGameplayEventToActor(
    AActor* Actor,          // Target actor receiving the event
    FGameplayTag EventTag,  // Tag identifying the event type (e.g., "Damage", "XP")
    FGameplayEventData Payload // Contextual data for the event
);
```

---

## **Key Parameters Explained**

| **Parameter** | **Description** |
| --- | --- |
| **`Actor`** | The actor to receive the event. Must have an **Ability System Component**. |
| **`EventTag`** | A gameplay tag (e.g., **`Attributes.Meta.IncomingXP`**) to route the event. |
| **`Payload`** | Structured data (e.g., damage value, XP amount) passed to triggered abilities. |

---

## **Example Usage**

*Grant XP to a character through an event:*

```cpp
// 1. Prepare payload data
FGameplayEventData Payload;
Payload.EventTag = GameplayTags.Attributes_Meta_IncomingXP; // Tag for XP events
Payload.Instigator = GetInstigator(); // Who granted the XP
Payload.Target = Props.SourceCharacter; // Who receives the XP
Payload.EventMagnitude = 50.f; // Amount of XP to grant

// 2. Send the event to the target actor
UAbilitySystemBlueprintLibrary::SendGameplayEventToActor(
    Props.SourceCharacter,     // AActor* receiving the event
    GameplayTags.Attributes_Meta_IncomingXP, // Event tag
    Payload                    // XP data
);
```

---

[`WaitGameplayEvent`](../../UAbilityTask_WaitGameplayEvent/UAbilityTask_WaitGameplayEvent/WaitGameplayEvent%2013d8d590ff3880c981f7f53423715402.md) 

## **Best Practices**

1. **Tag Setup**
    - Define event tags in your project's **Gameplay Tag Table** (e.g., **`Attributes.Meta.IncomingXP`**).
2. **Payload Data**
    
    Populate **`FGameplayEventData`** with relevant context:
    
    ```cpp
    Payload.ContextHandle = AbilitySystemComponent->MakeEffectContext(); // Optional effect context
    Payload.OptionalObject = ThisEffectClass; // Associated object (e.g., UGameplayEffect)
    ```
    
3. **Receiver Requirements**
    - The target actor **must** have an **`AbilitySystemComponent`** (ASC).
    - Abilities using **`AbilityTriggers`** with matching tags will activate automatically.
4. **Blueprint Access**CopyDownload
    
    Expose this function to designers via Blueprint:
    
    ```cpp
    // In Blueprint Function Library:
    UFUNCTION(BlueprintCallable, Category = "Abilities")
    static void SendXPToActor(AActor* Target, float XPAmount) { ... }
    ```
    

---

## **Common Use Cases**

- **XP/Currency Systems**: Grant XP/loot when interacting with objects.
- **Damage/Healing**: Trigger damage calculations with magnitude data.
- **Quest Events**: Notify abilities of quest progress updates.

---

## **Troubleshooting**

- **Event Not Triggering?**CopyDownload
    1. Verify the target actor has an **`AbilitySystemComponent`**.
    2. Confirm the ability uses **`Triggers`** matching the event tag.
    
    ```cpp
    // Ability setup example:
    UAbilityTask_WaitGameplayEvent* WaitEvent = UAbilityTask_WaitGameplayEvent::WaitGameplayEvent(
        this,
        GameplayTags.Attributes_Meta_IncomingXP // Listening for this tag
    );
    ```
    

---

This revision clarifies the function's role in ability-driven systems and provides actionable implementation guidance.