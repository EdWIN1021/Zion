**Ability Task** 是继承自 `UGameplayTask` 的类，专门用于 GAS 系统中，封装各种 **异步行为或监听逻辑**，比如

- 等待某个动画播放完成
- 等待输入（按键释放等）
- 等待某个时间段
- 等待特定事件（比如命中事件、碰撞事件）
- 播放特效、发出射线等

![[Screenshot 2025-06-24 164000.png]]


```cpp
UFUNCTION(BlueprintCallable, Category = "Warrior|AbilityTasks", meta=(DisplayName="Wait Gameplay Event And Spawn Enemies", HidePin = "OwningAbility", DefaultToSelf = "OwningAbility", BlueprintInternalUseOnly = "true", NumToSpawn = "1", RandomSpawnRadius = "200"))  
static UAbilityTask_WaitSpawnEnemies* WaitSpawnEnemies(  
    UGameplayAbility* OwningAbility,  
    FGameplayTag EventTag,  
    TSoftClassPtr<AWarriorEnemyCharacter> SoftEnemyClassToSpawn,  
    int32 NumToSpawn,  
    const FVector& SpawnOrigin,  
    float RandomSpawnRadius,  
    const FRotator& SpawnRotation);
```


```cpp
DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FWaitSpawnEnemiesDelegate, const TArray<AWarriorEnemyCharacter*>&, SpawnedEnemies);

UPROPERTY(BlueprintAssignable)  
FWaitSpawnEnemiesDelegate OnSpawnFinished;  
  
UPROPERTY(BlueprintAssignable)  
FWaitSpawnEnemiesDelegate DidNotSpawn;

```

---
## Override

```cpp
void UAbilityTask_WaitSpawnEnemies::Activate()  
{  
    /* 监听GameplayEventTag */  
    FGameplayEventMulticastDelegate& Delegate = AbilitySystemComponent->GenericGameplayEventCallbacks.FindOrAdd(CachedEventTag);  
    DelegateHandle = Delegate.AddUObject(this, &ThisClass::OnGameplayEventReceived);  
}
```

```cpp
void UAbilityTask_WaitSpawnEnemies::OnDestroy(bool bInOwnerFinished)  
{  
    FGameplayEventMulticastDelegate& Delegate = AbilitySystemComponent->GenericGameplayEventCallbacks.FindOrAdd(CachedEventTag);  
    Delegate.Remove(DelegateHandle);  
    Super::OnDestroy(bInOwnerFinished);  
}
```

```cpp
void UAbilityTask_WaitSpawnEnemies::OnGameplayEventReceived(const FGameplayEventData* InPayLoad)  
{  
    Debug::Print(TEXT("asdasdasdasdasd"));  
    EndTask();  
}
```