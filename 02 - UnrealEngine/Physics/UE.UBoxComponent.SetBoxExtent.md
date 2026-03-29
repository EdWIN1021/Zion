# SetBoxExtent

Access Specifier: public
Belongs to: UBoxComponent (../../UBoxComponent%201408d590ff38806aa03ae02e257e3b69.md) 
Tags: BlueprintCallable
Description: Change the box extent size. This is the unscaled size, before component scale is applied.

## **Declaration**

```cpp
/** 
	* @param	InBoxExtent: new extent (radius) for the box.
	* @param	bUpdateOverlaps: if true and this shape is registered and collides, updates touching array for owner actor.
  */
UFUNCTION(BlueprintCallable, Category="Components|Box")
ENGINE_API void SetBoxExtent(FVector InBoxExtent, bool bUpdateOverlaps=true);
```

## **Example**

```cpp
WeaponCollisionBox->SetBoxExtent(FVector(20.f));
```