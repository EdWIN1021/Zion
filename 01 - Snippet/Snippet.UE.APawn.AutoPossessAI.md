# AutoPossessAI

Category: Property

<aside>

Determines when the Pawn creates and is possessed by an AI Controller (on level start, when spawned, etc). Only possible if AIControllerClassRef is set, and ignored if AutoPossessPlayer is enabled.

</aside>

```cpp
UPROPERTY(EditAnywhere, Category=Pawn)
EAutoPossessAI AutoPossessAI;
```

```cpp
AutoPossessAI = EAutoPossessAI::PlacedInWorldOrSpawned;
```