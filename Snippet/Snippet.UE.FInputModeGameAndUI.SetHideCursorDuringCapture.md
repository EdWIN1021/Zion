# SetHideCursorDuringCapture

Description: Whether to hide the cursor during temporary mouse capture caused by a mouse down

```cpp
	FInputModeGameAndUI& SetHideCursorDuringCapture(bool InHideCursorDuringCapture) { bHideCursorDuringCapture = InHideCursorDuringCapture; return *this; }
```

```cpp
	InputModeData.SetHideCursorDuringCapture(false);
```