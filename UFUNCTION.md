- ExpandEnumAsExecs
    
    - OutValidType will be the out pin in blueprint funciton
    
    ```cpp
    UFUNCTION(BlueprintCallable, Category="Warrior|FunctionLibrary", meta = (DisplayName = "Get Pawn Combat Component From Actor", ExpandEnumAsExecs = "OutValidType"))
    static UPawnCombatComponent* BP_GetPawnCombatComponentFromActor(AActor* InActor, EWarriorValidType& OutValidType);
    ```
    
- BlueprintCallable
    
    ```cpp
    UFUNCTION(BlueprintCallable)
    ```
    
- BlueprintPure
    
    ```cpp
    FUNCTION(BlueprintPure)
    ```
    

### **BlueprintImplementableEvent**

- A **BlueprintImplementableEvent** in Unreal Engine is a type of function declared in C++ that allows Blueprints to provide their own implementation.
    - **Function Declaration**
        
        ```cpp
        // BlueprintImplementableEvent -> dont need to make virtual
        UFUNCTION(BlueprintImplementableEvent)
        void CreateFields(const FVector& FieldLocation);
        ```
        
    - Call the Blueprint-implemented event
        
        ```cpp
        CreateFields(BoxHit.ImpactPoint);
        ```
        
    - **Blueprint Implementation**
        
        ![屏幕截图 2025-04-17 174154.png](attachment:d1002dff-d7ab-4aff-8ae4-bc3a133080cb:%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-17_174154.png)
        

### BlueprintNativeEvent

- `BlueprintNativeEvent` is a **UFUNCTION specifier** used in C++ to declare a function that can have both a C++ implementation (default behavior) and an optional Blueprint override.
    
    ```cpp
    // Don't need virtual kayowrd 
    	UFUNCTION(BlueprintNativeEvent)
    	int32 GetPlayerLevel();
    ```
    
- Override the funciton
    
    ```cpp
    virtual void GetHit_Implementation(const FVector& ImpactPoint) override;
    ```
    
- Calla the function in C++
    
    ```cpp
    HitInterface->Execute_GetHit(BoxHit.GetActor(), BoxHit.ImpactPoint);
    ```
    

## NetMulticast

```cpp
UFUNCTION(NetMulticast, Reliable)
```

- Used to declare a **reliable multicast RPC (Remote Procedure Call)**
- `NetMulticast`: When the **server** calls this function, it executes **locally on the server** and is **replicated to all connected clients**.
- `Reliable`: The function is **guaranteed to arrive** at its destination, even if network conditions are poor.

## Meta

- HidePin
    
    ```cpp
    UFUNCTION(meta = (HidePin = "OwningAbility", DefaultToSelf = "OwningAbility", BlueprintInternalUseOnly = "true"))
    ```
    
- `BlueprintAssignable` is a specifier used to declare delegates that can be assigned or bound in Blueprints.
    
    ```cpp
    UPROPERTY(BlueprintAssignable)
    ```
    
- Runs on the **server** (must be called from the client).
    
    ```cpp
    UFUNCTION(Server, Reliable)
    ```
    
- Runs on the **client** (must be called from the server).
    
    ```cpp
    UFUNCTION(Client, Reliable)
    ```


```cpp
UPROPERTY(EditDefaultsOnly, BlueprintReadOnly, meta = (TitleProperty = "InputTag"))  
TArray<FWarriorInputActionConfig> NativeInputActions;
```