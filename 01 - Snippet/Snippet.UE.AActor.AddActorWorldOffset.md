---
Category: Function
---

> [!Tip]
> AddActorWorldOffset is a function in Unreal Engine that incrementally adjusts an actor’s location in world space by adding a specific offset vector.


```cpp
ENGINE_API void AddActorWorldOffset(FVector DeltaLocation, bool bSweep=false, FHitResult* OutSweepHitResult=nullptr, ETeleportType Teleport = ETeleportType::None);
```

```cpp
AddActorWorldOffset(FVector(1.0f, 0.0f, 0.0f));
```