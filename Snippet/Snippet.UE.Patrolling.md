# Patrolling

Tags: AI

## Overview

This section outlines the implementation details for enemy patrol behavior using AI navigation in a game project.

## Explanation

### 1. Enemy Controller Setup

```cpp
EnemyController = Cast<AAIController>(GetController());
if (EnemyController && PatrolTarget)
```

- `EnemyController` is cast from the enemy's controller.
- Checks if both `EnemyController` and `PatrolTarget` are valid.

---

### 2. AI Move Request Configuration

```cpp
FAIMoveRequest MoveRequest;
MoveRequest.SetGoalActor(PatrolTarget);
MoveRequest.SetAcceptanceRadius(15.f);
```

- Creates an `FAIMoveRequest` object.
- Sets the patrol target as the goal for the movement request.
- Configures an acceptance radius of 15 units (the AI will stop moving when within this distance from the target).

---

### 3. Path Calculation and Visualization

```cpp
FNavPathSharedPtr NavPath;
EnemyController->MoveTo(MoveRequest, &NavPath);

TArray<FNavPathPoint>& PathPoints = NavPath->GetPathPoints();

for (auto& Point : PathPoints)
{
    const FVector& Location = Point.Location;
    DrawDebugSphere(GetWorld(), Location, 12.0f, 12, FColor::Green, false, 10.f);
}
```

- Uses `EnemyController->MoveTo()` to initiate movement towards the patrol target.
- Retrieves the calculated navigation path (`NavPath`).
- Accesses all points in the path and visualizes them using green spheres.

---

## Notes:

1. This implementation assumes that `PatrolTarget` is already defined and set up elsewhere in your code.
2. The visualization (green spheres) helps debug and understand the patrol path during development.
3. Adjust parameters like `AcceptanceRadius` or sphere drawing properties as needed for your specific use case.