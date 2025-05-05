---
Category: Function
tags: 
Return Type:
---

```cpp
UWorld* World = GetWorld();  
  
if (World)  
{  
    APlayerController* Controller = World->GetFirstPlayerController();  
  
    if (Controller && SlashOverlayClass)  
    {  
       USlashOverlay* SlashOverlay = CreateWidget<USlashOverlay>(Controller, SlashOverlayClass);  
       SlashOverlay->AddToViewport();  
    }  
}
```

1. **Getting the World Context:**  
    - `UWorld* World = GetWorld();`  
    This line retrieves the world context from the current actor or component. It's essential for accessing player controllers and other game elements.
    
2. **Checking for a Valid World:**  
    - The outer `if (World)` ensures that we only proceed if the world is valid, preventing potential crashes or errors.
    
3. **Obtaining the Player Controller:**  
    - `APlayerController* Controller = World->GetFirstPlayerController();`  
    This retrieves the first player controller in the world, which is necessary for adding widgets to the viewport.
    
4. **Validating Dependencies:**  
    - The inner `if (Controller && SlashOverlayClass)` ensures both the player controller and the widget class are valid before attempting to create the widget.
    
5. **Creating and Adding the Widget:**
    - `CreateWidget` instantiates an object of the specified class (`SlashOverlayClass`) and associates it with the player controller.
    - `AddToViewport()` attaches the widget to the player's viewport, making it visible in-game.