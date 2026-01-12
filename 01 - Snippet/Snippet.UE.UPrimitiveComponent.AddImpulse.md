# AddImpulse

Access Specifier: public
Tags: Virtual

<aside>

- Add an impulse to a single rigid body. Good for one time instant burst.
</aside>

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Physics", meta=(UnsafeDuringActorConstruction="true"))
ENGINE_API virtual void AddImpulse(FVector Impulse, FName BoneName = NAME_None, bool bVelChange = false);

```

## **Example**

```cpp
GetMesh()->AddImpulse(DeathImpulse, NAME_None, true);
```