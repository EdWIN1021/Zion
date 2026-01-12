# HomingTargetComponent

Access Specifier: Public
Category: Property
Type: USceneComponent (../../USceneComponent%2013c8d590ff38805a918ff25ad6bf4a96.md)

<aside>

The current target we are homing towards. Can only be set at runtime (when projectile is spawned or updating).

</aside>

```cpp
UPROPERTY(VisibleInstanceOnly, BlueprintReadWrite, Category=Homing)
TWeakObjectPtr<USceneComponent> HomingTargetComponent;
```