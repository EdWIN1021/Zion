# GetLocalPlayer

Access Specifier: public
Description: Returns the ULocalPlayer for this controller if it exists, or null otherwise

## **Declaration**

```cpp
ENGINE_API class ULocalPlayer* GetLocalPlayer() const;
```

## **Example**

```cpp
UEnhancedInputLocalPlayerSubsystem* Subsystem = ULocalPlayer::GetSubsystem<UEnhancedInputLocalPlayerSubsystem>(GetLocalPlayer());
```