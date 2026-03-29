### Dominant Sense (主导感知)
- AISense_Hearing
- AISense_Sight


### Senses Config
- #### AI Sight config
	- Max Age (AI 记住看到目标的最长时间)

- #### AI Hearing config
	- Max Age

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