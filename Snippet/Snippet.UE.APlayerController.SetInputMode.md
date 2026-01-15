# SetInputMode

Access Specifier: public
Description: Setup an input mode

## **Declaration**

```cpp
ENGINE_API virtual void SetInputMode(const FInputModeDataBase& InData);
```

## **Example**

```cpp
FInputModeGameAndUI InputModeData;
InputModeData.SetLockMouseToViewportBehavior(EMouseLockMode::DoNotLock);
InputModeData.SetHideCursorDuringCapture(false);
SetInputMode(InputModeData);
```