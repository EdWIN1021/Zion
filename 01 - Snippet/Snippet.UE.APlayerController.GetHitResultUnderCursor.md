# GetHitResultUnderCursor

Access Specifier: public
Tags: BlueprintCallable

## **Declaration**

```cpp
UFUNCTION(
BlueprintCallable,
Category="Game|Player",
meta=(DeprecatedFunction,
DeprecationMessage = "Use new GetHitResultUnderCursorByChannel or GetHitResultUnderCursorForObject",
TraceChannel=ECC_Visibility, bTraceComplex=true)
)
bool GetHitResultUnderCursor(ECollisionChannel TraceChannel, bool bTraceComplex, FHitResult& HitResult) const
```

## **Example**

```cpp
FHitResult CursorHit; 
GetHitResultUnderCursor(ECC_Visibility, false, CursorHit);
```