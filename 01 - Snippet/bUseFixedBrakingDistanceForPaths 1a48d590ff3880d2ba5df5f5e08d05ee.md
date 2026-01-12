# bUseFixedBrakingDistanceForPaths

Access Specifier: Protected
Tags: Property

<aside>

- When enabled, this option ensures that a character will start slowing down (braking) at a fixed distance before reaching its destination, rather than dynamically adjusting the braking distance based on velocity.
</aside>

```cpp
	UPROPERTY(EditAnywhere, Category = NavMovement, meta = (EditCondition = "bUseAccelerationForPaths"))
	uint8 bUseFixedBrakingDistanceForPaths : 1;
```