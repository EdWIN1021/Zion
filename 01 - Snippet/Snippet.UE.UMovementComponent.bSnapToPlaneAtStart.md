# bSnapToPlaneAtStart

Access Specifier: public
Description: If true and plane constraints are enabled, then the updated component will be snapped to the plane when first attached.

```cpp
UPROPERTY(EditAnywhere, BlueprintReadOnly, Category=PlanarMovement, meta=(editcondition=bConstrainToPlane))
uint8 bSnapToPlaneAtStart:1;
```

```cpp
	GetCharacterMovement()->bSnapToPlaneAtStart = true;
```