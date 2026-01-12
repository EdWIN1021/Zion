# Tracing

- Line Tracing
    
    ![屏幕截图 2025-04-15 180732.png](Tracing/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-15_180732.png)
    
- Sphere Tracing
    
    ![屏幕截图 2025-04-15 180656.png](Tracing/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-15_180656.png)
    
- Box Tracing
    
    ![屏幕截图 2025-04-15 180528.png](Tracing/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-15_180528.png)
    

![屏幕截图 2025-04-15 200314.png](Tracing/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-15_200314.png)

- Trace Channel
    - Visibility
        - The Visibility channel is designed to represent what would logically block a “line of sight”—for example, walls, floors, or other solid pieces of geometry.
        - Objects that are meant to be seen in the scene are usually set so that their collision response on the Visibility channel is to block.
    

### Create two [`*USceneComponent*`](https://www.notion.so/USceneComponent-13c8d590ff38805a918ff25ad6bf4a96?pvs=21)

```cpp
UPROPERTY(VisibleAnywhere)
USceneComponent* BoxTraceStart;

UPROPERTY(VisibleAnywhere)
USceneComponent* BoxTraceEnd;
```

### Box Trace

```cpp
	const FVector Start = BoxTraceStart->GetComponentLocation();
	const FVector End = BoxTraceEnd->GetComponentLocation();
	
	TArray<AActor*> ActorsToIgnore;
	ActorsToIgnore.Add(this);
	ActorsToIgnore.Add(GetOwner());

	FHitResult BoxHit;
	UKismetSystemLibrary::BoxTraceSingle(
	this,
	Start,
	End,
	FVector(5.f, 5.f,5.f),
	BoxTraceStart->GetComponentRotation(),
	ETraceTypeQuery::TraceTypeQuery1,
	false,
	ActorsToIgnore,
	EDrawDebugTrace::ForDuration,
	BoxHit,
	true
	);
```