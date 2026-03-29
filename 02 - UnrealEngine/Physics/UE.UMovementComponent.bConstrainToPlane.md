# bConstrainToPlane

Access Specifier: public
Description: If true, movement will be constrained to a plane

```cpp
UPROPERTY(EditAnywhere, BlueprintReadOnly, Category=PlanarMovement)
uint8 bConstrainToPlane:1;
```

```cpp
	GetCharacterMovement()->bConstrainToPlane = true;
```