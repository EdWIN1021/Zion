# InitAbilityActorInfo

Tags: virtual
Description: Initialized the Abilities' ActorInfo - the structure that holds information about who we are acting on and who controls us.

- OwnerActor is the actor that logically owns this component.
- AvatarActor is what physical actor in the world we are acting on.
- Usually a Pawn but it could be a Tower, Building, Turret, etc, may be the same as Owner

## **Declaration**

```cpp
virtual void InitAbilityActorInfo(AActor* InOwnerActor, AActor* InAvatarActor);
```

## **Example**

```cpp
AuraPlayerState->GetAbilitySystemComponent()->InitAbilityActorInfo(AuraPlayerState, this);
```