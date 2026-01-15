# SpawnActorDeferred

Access Specifier: public
Description: Allowing you to modify properties or set up the actor before it's fully initialized and added to the level

## **Declaration**

```cpp
template< class T > 	
T* SpawnActorDeferred( 		
	UClass* Class, 		
	FTransform const& Transform, 		
	AActor* Owner = nullptr, 		
	APawn* Instigator = nullptr, 		
	ESpawnActorCollisionHandlingMethod CollisionHandlingOverride = ESpawnActorCollisionHandlingMethod::Undefined,
	ESpawnActorScaleMethod TransformScaleMethod = ESpawnActorScaleMethod::MultiplyWithRoot){ 		
	if( Owner ) 		{ 			
		check(this==Owner->GetWorld()); 		
	} 		
	FActorSpawnParameters SpawnInfo; 		
	SpawnInfo.SpawnCollisionHandlingOverride = CollisionHandlingOverride; 		
	SpawnInfo.TransformScaleMethod = TransformScaleMethod; 		
	SpawnInfo.Owner = Owner; 		
	SpawnInfo.Instigator = Instigator; 		
	SpawnInfo.bDeferConstruction = true; 		
	return (Class != nullptr) ? Cast<T>(SpawnActor(Class, &Transform, SpawnInfo)) : nullptr; 	
	}
```

## **Example**

```cpp
AuraProjectile* Projectile = GetWorld()->SpawnActorDeferred<AAuraProjectile>(
	ProjectileClass, 	
	SpawnTransform, 	
	GetOwningActorFromActorInfo(), 	
	Cast<APawn>(GetOwningActorFromActorInfo()), 	
	ESpawnActorCollisionHandlingMethod::AlwaysSpawn
);
```