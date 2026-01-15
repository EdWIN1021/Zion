# Activate

Category: Function

```cpp
	UFUNCTION(BlueprintCallable, Category="Components|Activation", meta=(UnsafeDuringActorConstruction="true"))
	ENGINE_API virtual void Activate(bool bReset=false);
```

```cpp
LevelUpNiagaraComponent->Activate(true);
```