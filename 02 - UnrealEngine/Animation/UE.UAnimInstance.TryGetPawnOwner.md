# TryGetPawnOwner

Access Specifier: public
Description: Returns the APawn that owns the USkeletalMeshComponent associated with the UAnimInstance.
Tags: Function

```cpp
	UFUNCTION(BlueprintCallable, Category = "Animation") 
	ENGINE_API virtual APawn* TryGetPawnOwner() const;
```

```cpp
APawn* PawnOwner = TryGetPawnOwner();
```