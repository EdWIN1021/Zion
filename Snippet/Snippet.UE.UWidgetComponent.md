---
Base: "[[Concept.UE.AActor]]"
---
Used to **display UI in the 3D world**, hosting a `UUserWidget` in the game world.

```cpp
PublicDependencyModuleNames.AddRange(new[] { "UMG" });
```

```cpp
UPROPERTY(VisibleAnywhere, BlueprintReadOnly)
TObjectPtr<UWidgetComponent> HealthBar;
```

```cpp
UAuraUserWidget* AuraUserWidget = Cast<UAuraUserWidget>(HealthBar->GetUserWidgetObject())
```