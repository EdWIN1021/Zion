## Overview

This section outlines the implementation details for a timer-based patrol system in a game project.

## Explanation

### 1. Timer Handle Declaration

```cpp
FTimerHandle PatrolTimer;
```

- Declares a timer handle to keep track of the active timer.

---

### 2. Timer Callback Function

```cpp
void PatrolTimerFinished();
```

- Defines an empty callback function that will be triggered when the timer completes.
- You'll need to implement this function to define what happens when the timer finishes (e.g., triggering patrol behavior).

---

### 3. Setting Up the Timer

```cpp
GetWorldTimerManager().SetTimer(PatrolTimer, this, &AEnemy::PatrolTimerFinished, 5.f);
```

- Uses `GetWorldTimerManager()` to access the world's timer manager.
- Sets up a new timer using:
    - `PatrolTimer`: The handle for the newly created timer.
    - `this`: The object that owns the callback function.
    - `&AEnemy::PatrolTimerFinished`: The callback function to execute when the timer completes.
    - `5.f`: The interval in seconds (every 5 seconds, this timer will trigger).

---

```cpp
GetWorldTimerManager().ClearTimer(PatrolTimer);
```

## Notes:

1. This implementation assumes that `PatrolTimer` is a member variable of your enemy class.
2. You'll need to implement the `PatrolTimerFinished()` function to define what happens when the timer completes.
3. Adjust the interval (`5.f`) as needed for your specific use case.



### Step-by-Step Explanation

1. **Declare the Timer Handle as a Member Variable**
    
    In your enemy class header file (e.g., `AEnemy.h`), declare a member variable to hold the timer handle:
    
    ```cpp
    class AEnemy : public Actor{
        GENERATED_BODY()
    
    public:
        // Other declarations...
    
        /** Timer handle for patrol system */
        FTimerHandle PatrolTimer;
    };
    
    ```
    
2. **Define the Callback Function**
    
    Implement the callback function that will be triggered when the timer completes. This function will define what happens when the patrol timer finishes, such as moving the enemy or changing its behavior:
    
    ```cpp
    void AEnemy::PatrolTimerFinished()
    {
        // Implementation of patrol behavior goes here.
        // For example, you might move the enemy to a new location or change its direction.
        if (IsAlive())
        {
            // Trigger patrol movement
            MoveToRandomLocation();
        }
    }
    
    ```
    
3. **Set Up the Timer in Your Enemy Class**
    
    In your enemy class's constructor or initialization function, set up the timer using the `GetWorldTimerManager()`:
    
    ```cpp
    void AEnemy::BeginPlay()
    {
        Super::BeginPlay();
    
        // Set up patrol timer
        GetWorldTimerManager().SetTimer(PatrolTimer, this, &AEnemy::PatrolTimerFinished, 5.f);
    }
    
    ```
    
4. **Clear the Timer When Necessary**
    
    If you need to stop the patrol behavior at any point (e.g., when the enemy is destroyed or stops patrolling), clear the timer:
    
    ```cpp
    void AEnemy::StopPatrol()
    {
        GetWorldTimerManager().ClearTimer(PatrolTimer);
    }
    
    ```
    
5. **Implement Patrol Behavior**
    
    Define the `MoveToRandomLocation()` function to handle the patrol movement. This function can move the enemy to a random location within a specified range:
    
    ```cpp
    void AEnemy::MoveToRandomLocation()
    {
        FVector CurrentLocation = GetActorLocation();
        FVector RandomDirection = UKismetMathLibrary::RandomUnitVector() * 100.0f; // Move within a 100-unit radius
        FVector NewLocation = CurrentLocation + RandomDirection;
    
        // Move the enemy to the new location
        GetWorld()->GetAuthenticator().MoveActor(this, NewLocation);
    }
    
    ```
    
6. **Adjust Timer Interval**
    
    Modify the interval parameter in `SetTimer` to adjust how frequently the patrol occurs. For example, changing it to 10 seconds would make the enemy patrol less frequently:
    
    ```cpp
    GetWorldTimerManager().SetTimerPatrolTimerFinished, 10.0f;
    
    ```