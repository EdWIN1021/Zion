# SetMaterial

Access Specifier: public
Description: Changes the material applied to an element of the mesh

## **Declaration**

```cpp
	/**
	 * @param ElementIndex - The element to access the material of.
	 * @return the material used by the indexed element of this mesh.
	 */

UFUNCTION(BlueprintCallable, Category="Rendering|Material")
ENGINE_API virtual void SetMaterial(int32 ElementIndex, class UMaterialInterface* Material);
```

## **Example**

```cpp

```