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