# GetRootComponent

Category: Function
Description: Returns this actor's root component

## **Declaration**

```cpp
FORCEINLINE USceneComponent* GetRootComponent() const { return RootComponent; }
```

## **Example**

```cpp
BridMesh->SetupAttachment(GetRootComponent());
```