# Delegates

<aside>
💡

A **delegate** is a type of object that allows you to define and manage callbacks or event-driven programming.

</aside>

[@Delegates ](Delegates/@Delegates%201878d590ff38808197b0fe4df25e13a0.csv)

## Single-cast Delegates **(1-to-1 binding)**

- **Declaration**
    
    Use **`DECLARE_DELEGATE_*`** macros for single-function binding.
    
    ```cpp
    DECLARE_DELEGATE_OneParam(FOnTargetInteractedDelegate, AActor*);
    ```
    

- Define the delegate instance
    
    ```cpp
    FOnTargetInteractedDelegate OnWeaponHitTarget;
    ```
    

- **Binding**
    
    Bind via **`BindUObject`** or **`BindLambda`** (supports only one function).
    
    ```cpp
    InWeaponToRegister->OnWeaponHitTarget.BindUObject(this, &ThisClass::OnHitTargetActor);
    ```
    

- **Execution**
    
    Call **`Execute`** or **`ExecuteIfBound`** (safe check).
    
    ```cpp
    OnWeaponHitTarget.ExecuteIfBound(OtherActor); // pass OtherActor to OnHitTargetActor callback function
    ```
    

## **Dynamic Multicast Delegates (Blueprint-compatible, 1-to-many binding)**

- **Declaration**
    
    Use **`DECLARE_DYNAMIC_MULTICAST_DELEGATE_*`** for Blueprint-friendly delegates.
    
    ```cpp
    DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FMultiplayerOnCreateSessionComplete, bool, bWasSuccessful);
    ```
    

- **Instance Declaration**
    
    Define the delegate instance:
    
    ```cpp
    UPROPERTY(BlueprintAssignable)
    FMultiPlayerOnCreateSessionComplete MultiPlayerOnCreateSessionComplete;
    ```
    

- **Binding**
    
    Use **`AddUniqueDynamic`**  to prevent duplicate bindings:
    
    ```cpp
    MultiplayerSessionsSubsystem->MultiPlayerOnCreateSessionComplete.AddUniqueDynamic(
     this, &UMenu::OnCreateSession  // Ensures one-time binding
    );
    ```
    

- **Broadcast**
    
    Trigger all bound functions:
    
    ```cpp
    MultiPlayerOnCreateSessionComplete.Broadcast(false);
    ```
    

| AddDynamic | AddUniqueDynamic |
| --- | --- |
| Binds multiple times → Duplicate calls | Prevent duplicates |
| Risk of dangling pointers | Safer with uniqueness check |
| Works but risky | Recommended for event-driven logic |

## Multi-cast Delegates (C++-only, 1-to-many binding)

- **Declaration**
    
    Use **`DECLARE_MULTICAST_DELEGATE_*`** macros:
    
    ```cpp
    DECLARE_MULTICAST_DELEGATE_OneParam(FOnPLayerStateChanged, int32 /*StatValue*/)
    DECLARE_MULTICAST_DELEGATE_TwoParams(FMultiplayerOnFindSessionsComplete, const TArray<FOnlineSessionSearchResult>& SessionResults, bool bWasSuccessful);  
    ```
    

- **Instance Declaration**
    
    Define the delegate instance:
    
    ```cpp
    FOnPLayerStateChanged OnXPChangedDelegate;
    ```
    

- **Binding**
    
    Use **`AddUObject`**/**`AddStatic`** for C++ logic:
    
    ```cpp
    AuraPlayerState->OnXPChangedDelegate.AddUObject(this, &UOverlayWidgetController::OnXPChanged);
    ```
    

- **Broadcast**
    
    Trigger all bound functions:
    
    ```cpp
    OnXPPercentChangedDelegate.Broadcast(XPBarPercent);	
    ```
    

 ****