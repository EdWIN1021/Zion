---
Class: "[[_temp_/Unreal/Types/Class/AActor/AActor]]"
Category: Function
Description:
Return Type:
---
## **Declaration**

```cpp
template <class T> T* GetInstigator() const { return Cast<T>(GetInstigator()); }
```

## **Example**

```cpp
APawn* WeaponOwningPawn = GetInstigator<APawn>();
```
