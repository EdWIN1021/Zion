# Detour Crowd Avoidance

Tags: AI

```cpp
ai.crowd.DebugSelectedActors 1

Project Settings -> Engine -> Crowd Manager
```

- Aware of other agents
- Alters velocity for new path
- Respects nav mesh

```cpp
AWarriorAIController::AWarriorAIController(const FObjectInitializer& ObjectInitializer)
	: Super(ObjectInitializer.SetDefaultSubobjectClass<UCrowdFollowingComponent>("PathFollowingComponent"))
{
	if (UCrowdFollowingComponent* CrowdComp = Cast<UCrowdFollowingComponent>(GetPathFollowingComponent()))
	{
			CrowdComp->SetCrowdSimulationState(bEnableDetourCrowdAvoidance ? ECrowdSimulationState::Enabled: ECrowdSimulationState::Disabled);
			CrowdComp->SetCrowdAvoidanceQuality(ECrowdAvoidanceQuality::Low); 
			
			CrowdComp->SetAvoidanceGroup(1);
			CrowdComp->SetGroupsToAvoid(1);
			CrowdComp->SetCrowdCollisionQueryRange(CollisionQueryRange);
	}
}
```