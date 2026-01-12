# Implementing Team System

## PlayerController

**Add Team ID Member Variable**

```cpp
FGenericTeamId HeroTeamId;  // Stores team affiliation (0 = default team)
```

**Initialize Team ID in Constructor**

```cpp
AWarriorHeroController::AWarriorHeroController()
{
    HeroTeamId = FGenericTeamId(0);  // Initialize to team ID 0
}
```

 **Implement Interface in Class Declaration**

```cpp
// Header file (WarriorHeroController.h)
class AWarriorHeroController : public APlayerController, 
                               public IGenericTeamAgentInterface
{
    // ... rest of class definition
}
```

**Override Interface Method**

```cpp
virtual FGenericTeamId GetGenericTeamId() const override;
```

**Implement Team ID Getter**

```cpp
FGenericTeamId AWarriorHeroController::GetGenericTeamId() const
{
    return HeroTeamId;  // Return current team ID
}
```

---

## **AI Controller**

**Class Declaration Additions**

```cpp
virtual ETeamAttitude::Type GetTeamAttitudeTowards(const AActor& Other) const override;
```

**Team Attitude Implementation**

```cpp
ETeamAttitude::Type AWarriorAIController::GetTeamAttitudeTowards(
    const AActor& Other) const
{
    // Safely check if Other is a pawn with a team interface
    if (const APawn* OtherPawn = Cast<APawn>(&Other)) 
    {
        if (const IGenericTeamAgentInterface* TeamAgent = 
            Cast<IGenericTeamAgentInterface>(OtherPawn->GetController()))
        {
            // Compare team IDs (1 vs 0 creates player vs AI opposition)
            return (TeamAgent->GetGenericTeamId() == GetGenericTeamId())
                ? ETeamAttitude::Friendly
                : ETeamAttitude::Hostile;
        }
    }
    
    // Default to Neutral for non-team actors
    return ETeamAttitude::Neutral; 
}
```

**Team Configuration in Constructor**

```cpp
// WarriorAIController.cpp
AWarriorAIController::AWarriorAIController()
{
    SetGenericTeamId(FGenericTeamId(1));  // AI belongs to team 1
}
```