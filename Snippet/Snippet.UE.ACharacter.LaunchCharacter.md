# LaunchCharacter

Access Specifier: public
Tags: funciton

<aside>

Set a pending launch velocity on the Character. This velocity will be processed on the next CharacterMovementComponent tick, and will set it to the "falling" state.

 Triggers the OnLaunched event. 

@PARAM LaunchVelocity is the velocity to impart to the Character 

@PARAM bXYOverride if true replace the XY part of the Character's velocity instead of adding to it. 

@PARAM bZOverride if true replace the Z component of the Character's velocity instead of adding to it.

</aside>

```cpp
	UFUNCTION(BlueprintCallable, Category=Character)
	ENGINE_API virtual void LaunchCharacter(FVector LaunchVelocity, bool bXYOverride, bool bZOverride);
```

```cpp
Props.TargetCharacter->LaunchCharacter(KnockbackForce, true, true);
```