---
Category: Function
---

```cpp
ENGINE_API void FinishSpawning(
	const FTransform& Transform,  	
	bool bIsDefaultTransform = false,  	
	const FComponentInstanceDataCache* InstanceDataCache = nullptr,  	
	ESpawnActorScaleMethod TransformScaleMethod = ESpawnActorScaleMethod::OverrideRootScale
);
```

```cpp
Projectile->FinishSpawning(SpawnTransform);
```