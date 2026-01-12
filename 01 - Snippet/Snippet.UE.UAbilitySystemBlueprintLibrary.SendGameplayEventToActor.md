---
id: SendGameplayEventToActor
aliases: []
tags: []
Category: Funciton
---


```cpp
FGameplayEventData EventData;
EventData.Instigator = GetOwningPawn();
EventData.Target = HitActor;

UAbilitySystemBlueprintLibrary::SendGameplayEventToActor( GetOwningPawn(), WarriorGameplayTags::Shared_Event_MeleeHit, EventData );
```
