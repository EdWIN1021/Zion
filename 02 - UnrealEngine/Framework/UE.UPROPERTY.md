# UPROPERTY

Type: Macro

```cpp
/* The UPROPERTY() macro is used to mark a variable so that Unreal Engine's reflection system is aware of it */

UPROPERTY()
TObjectPtr<UAbilitySystemComponent> AbilitySystemComponent;
```

## Transient

```cpp
/*
 * 这个变量不会被序列化到磁盘上，也不会保存到存档/蓝图/关卡里
 * 临时变量，只在运行时存在
 */
 
UPROPERTY(Transient)
TMap<FGameplayTag, UCommonActivatableWidgetContainerBase* > RegisteredWidgetStackMap;
```

## Exposing Variables to Blueprint

```cpp
// EditDefaultsOnly: blueprint 
UPROPERTY(EditDefaultsOnly)

// EditInstanceOnly: instance 
UPROPERTY(EditInstanceOnly)

// EditAnywhere: both blueprint and instance
UPROPERTY(EditAnywhere)

// VisibleDefaultOnly: blueprint 
UPROPERTY(VisibleDefaultOnly)

// VisibleInstanceOnly: instance 
UPROPERTY(VisibleInstanceOnly)

// VisibleAnywhere: both blueprint and instance
UPROPERTY(VisibleAnywhere)
```

## Exposing Variables to the Event Graph

```cpp
// get / cannot be private
UPROPERTY(BlueprintReadOnly)

// set
UPROPERTY(BlueprintReadWrite)
```

## Category

```cpp
	UPROPERTY(BlueprintReadOnly, Category = Movement)
	bool IsFalling;

	UPROPERTY(BlueprintReadOnly, Category = "Movement | Character State")
	ECharacterState CharacterState;
```

## Meta

- AllowPrivateAccess
    
    ```cpp
    UPROPERTY(BlueprintReadOnly, meta=(AllowPrivateAccess = "true"))
    ```
    

- BindWidget
    - `BindWidget` is a meta tag used with `UPROPERTY` to instruct Unreal’s UMG system to bind a C++ pointer variable to a widget instance in a Blueprint subclass of `UUserWidget`.
    - The critical rule for `BindWidget` to succeed is that the C++ variable name must exactly match the name of the widget in the Blueprint (including case).
        
        ```cpp
        
        UPROPERTY(meta = (BindWidget))
        class UTextBlock* DisplayText;
        ```
        
- Replicated
    
    ```cpp
    // The UPROPERTY(Replicated) macro in Unreal Engine is used to mark a variable for **network replication**, ensuring its value is synchronized from the server to all connected clients in a multiplayer game.
    UPROPERTY(Replicated)
    UPROPERTY(ReplicatedUsing = OnRep_Health)
    
    ```
    
- ExposeOnSpawn
    
    ```cpp
    UPROPERTY(meta=(ExposeOnSpawn = true))
    ```