# GetBlackboardComponent

Access Specifier: public
Belongs to: AAIController (../../AAIController%201378d590ff3880878befd6ffe1950388.md)

## **Declaration**

```cpp
UBlackboardComponent* GetBlackboardComponent() { return Blackboard; }
```

## **Example**

```cpp
AuraAIController->GetBlackboardComponent()->InitializeBlackboard(*BehaviorTree->BlackboardAsset);
```

```cpp
UFUNCTION(BlueprintCallable, Category = "AI") AIMODULE_API virtual bool RunBehaviorTree(UBehaviorTree* BTAsset);
```


```cpp
AuraAIController->RunBehaviorTree(BehaviorTree);
```


