# GetFirstLocalPlayerFromController

Access Specifier: public
Description: Get the first valid local player via the first player controller

## **Declaration**

```cpp
ULocalPlayer* GetFirstLocalPlayerFromController() const;
```

## **Example**

```cpp
const ULocalPlayer* LocalPlayer = GetWorld()->GetFirstLocalPlayerFromController();
```