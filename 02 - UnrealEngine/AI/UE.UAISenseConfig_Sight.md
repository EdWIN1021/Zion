# UAISenseConfig_Sight

System: AI
Type: Class

<aside>

[UObject](UObject%201378d590ff3880b19696d9852e8a88d8.md) → [`UAISenseConfig`](UAISenseConfig%201f88d590ff3880119cd9e794f41aaeb0.md) → [`UAISenseConfig_Sight`](UAISenseConfig_Sight%201f88d590ff388030a3b5d6229bbf2689.md) 

</aside>

```cpp
UPROPERTY(VisibleAnywhere, BlueprintReadOnly)
UAISenseConfig_Sight* AISenseConfig_Sight;
```

```cpp
	AISenseConfig_Sight = CreateDefaultSubobject<UAISenseConfig_Sight>("EnemySenseConfig_Sight");
	AISenseConfig_Sight->DetectionByAffiliation.bDetectEnemies = true;
	AISenseConfig_Sight->DetectionByAffiliation.bDetectFriendlies = false;
	AISenseConfig_Sight->DetectionByAffiliation.bDetectNeutrals = false;
	AISenseConfig_Sight->SightRadius = 5000.f;
	AISenseConfig_Sight->LoseSightRadius = 0.f;
	AISenseConfig_Sight->PeripheralVisionAngleDegrees = 360.f;
```