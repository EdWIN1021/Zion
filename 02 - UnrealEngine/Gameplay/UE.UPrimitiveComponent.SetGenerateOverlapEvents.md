# SetGenerateOverlapEvents

Access Specifier: public
Description: Modifies value returned by GetGenerateOverlapEvents()
Tags: BlueprintSetter

## **Declaration**

```cpp
UFUNCTION(BlueprintSetter)
ENGINE_API void SetGenerateOverlapEvents(bool bInGenerateOverlapEvents);
```

## **Example**

```cpp
GetMesh()->SetGenerateOverlapEvents(true);
```