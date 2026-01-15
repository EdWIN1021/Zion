# RunBehaviorTree

Access Specifier: public
Belongs to: AAIController (../../AAIController%201378d590ff3880878befd6ffe1950388.md) 
Description: Starts executing behavior tree.
Tags: BlueprintCallable

## **Declaration**

```cpp
UFUNCTION(BlueprintCallable, Category = "AI")
AIMODULE_API virtual bool RunBehaviorTree(UBehaviorTree* BTAsset);
```

## **Example**

```cpp
AuraAIController->RunBehaviorTree(BehaviorTree);
```