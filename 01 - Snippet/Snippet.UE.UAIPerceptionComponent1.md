# UAIPerceptionComponent

System: AI
Type: Class

<aside>

[UObject](UObject%201378d590ff3880b19696d9852e8a88d8.md) →  [**UActorComponent**](UActorComponent%2013c8d590ff388034b1ead8167ef4e4cc.md) → [`UAIPerceptionComponent`](UAIPerceptionComponent%201f88d590ff388013bb15f2a9d7a79674.md) 

</aside>

```cpp
UPROPERTY(VisibleAnywhere, BlueprintReadOnly)
UAIPerceptionComponent* EnemyPerceptionComponent;
```

```cpp
EnemyPerceptionComponent = CreateDefaultSubobject<UAIPerceptionComponent>("EnemyPerceptionComponent");
EnemyPerceptionComponent->ConfigureSense(*AISenseConfig_Sight);
EnemyPerceptionComponent->SetDominantSense(UAISenseConfig_Sight::StaticClass());
EnemyPerceptionComponent->OnTargetPerceptionUpdated.AddUniqueDynamic(this, &ThisClass::OnEnemyPerceptionUpdated);
```