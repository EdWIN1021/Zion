---
Category: Function
---
> [!NOTE] Title
> returns the **last input vector** used to control the pawn's movement. This vector represents the direction and magnitude of the movement input applied to the pawn, such as from player input (e.g., WASD keys) or AI logic.

```cpp
UFUNCTION(BlueprintCallable, Category="Pawn|Input", meta=(Keywords="GetMovementInput GetInput"))  
ENGINE_API FVector GetLastMovementInputVector() const;
```




