# FinishSpawning-

Category: Function

## **Declaration**

```cpp
ENGINE_API void FinishSpawning(
	const FTransform& Transform,  	
	bool bIsDefaultTransform = false,  	
	const FComponentInstanceDataCache* InstanceDataCache = nullptr,  	
	ESpawnActorScaleMethod TransformScaleMethod = ESpawnActorScaleMethod::OverrideRootScale
);
```

## **Example**

```cpp
Projectile->FinishSpawning(SpawnTransform);
```