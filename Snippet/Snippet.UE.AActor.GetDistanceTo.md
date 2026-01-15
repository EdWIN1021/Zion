# GetDistanceTo

Category: Function

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "Transformation")  
ENGINE_API float GetDistanceTo(const AActor* OtherActor) const;
```

## **Example**

```cpp
const float Distance = OwningPawn->GetDistanceTo(Actor);
```