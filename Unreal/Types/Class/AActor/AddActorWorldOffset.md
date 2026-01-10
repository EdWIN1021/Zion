---
Class: "[[Unreal/Types/Class/AActor/AActor]]"
Category: Function
Description: incrementally adjusts an actor’s location in world space by adding a specific offset vector
Return Type:
---
## **Declaration**

```cpp
ENGINE_API void AddActorWorldOffset(FVector DeltaLocation, bool bSweep=false, FHitResult* OutSweepHitResult=nullptr, ETeleportType Teleport = ETeleportType::None);

```

## **Example**

```cpp
AddActorWorldOffset(FVector(1.0f, 0.0f, 0.0f));
```
