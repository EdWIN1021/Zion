# ReceiveExecuteAI

Access Specifier: Public
Category: function
Tags: BlueprintImplementableEvent

<aside>

- Called when the task starts executing in the Behavior Tree.
</aside>

```cpp
UFUNCTION(BlueprintImplementableEvent, Category = AI)
AIMODULE_API void ReceiveExecuteAI(AAIController* OwnerController, APawn* ControlledPawn);
```