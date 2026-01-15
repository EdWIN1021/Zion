# OverlapMultiByObjectType

Access Specifier: public
Description: Test the collision of a shape at the supplied location using object types, and determine the set of components that it overlaps

## **Declaration**

```cpp
/**
	*  @param  OutOverlaps        Array of components found to overlap supplied box
	*  @param  Pos                Location of center of shape to test against the world
	*	 @param	ObjectQueryParams	  List of object types it's looking for
	*  @param	CollisionShape	    CollisionShape - supports Box, Sphere, Capsule
	*  @param  Params             Additional parameters used for the trace
	*  @return TRUE if any overlap is found
	*/
bool OverlapMultiByObjectType(TArray<struct FOverlapResult>& OutOverlaps, const FVector& Pos, const FQuat& Rot, const FCollisionObjectQueryParams& ObjectQueryParams, const FCollisionShape& CollisionShape, const FCollisionQueryParams& Params = FCollisionQueryParams::DefaultQueryParam) const;
```

## **Example**

```cpp
World->OverlapMultiByObjectType(Overlaps,
		                            SphereOrigin,
		                            FQuat::Identity,
		                            FCollisionObjectQueryParams(
			                          FCollisionObjectQueryParams::InitType::AllDynamicObjects),
		                            FCollisionShape::MakeSphere(Radius), SphereParams);
```