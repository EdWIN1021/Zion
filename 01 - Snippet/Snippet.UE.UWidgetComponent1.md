# UWidgetComponent

Base: UMeshComponent (UMeshComponent%201898d590ff388008afa4c8bd5edce4e4.md) 
Type: Class

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