# SetSimulatePhysics

Access Specifier: public
Description: Sets whether or not a single body should use physics simulation, or should be 'fixed' (kinematic)

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category="Physics")
ENGINE_API virtual void SetSimulatePhysics(bool bSimulate);
```

## **Example**

```cpp
GetMesh()->SetSimulatePhysics(true);
```