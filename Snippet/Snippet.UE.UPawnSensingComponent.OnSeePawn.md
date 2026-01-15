# OnSeePawn

Category: Event

<aside>

This is a callback event that occurs when the pawn detects another pawn within its sensing range. The `SeenPawn` parameter contains the pawn that was detected.

</aside>

```cpp
void AEnemy::BeginPlay()
{
    super::BeginPlay();
    
    // Add the callback for when a pawn is detected
    if (PawnSensing)
    {
        PawnSensing->OnSeePawn.AddDynamic(this, &AEnemy::PawnSeen);
    }
}

void AEnemy::PawnSeen(APawn* SeenPawn)
{
    // Implement custom logic here when a pawn is detected
    UE_LOG(LogTemp, Log, TEXT("Enemy saw pawn: %s"), *SeenPawn->GetName());
}
```