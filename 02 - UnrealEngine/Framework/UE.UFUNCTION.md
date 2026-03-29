# UFUNCTION

Type: Macro

## BlueprintCallable

- It tells the engine that **this C++ function can be called from Blueprints**

```cpp
UFUNCTION(BlueprintCallable)
void RegisterCreatedPrimaryLayoutWidget(UWidget_PrimaryLayout* InCreatedWidget);
```

---

ExpandEnumAsExecs 

- OutValidType will be the out pin in blueprint funciton

```cpp
UFUNCTION(BlueprintCallable, 
					Category="Warrior|FunctionLibrary", 
					meta = (DisplayName = "Get Pawn Combat Component From Actor", ExpandEnumAsExecs = "OutValidType"))
static UPawnCombatComponent* BP_GetPawnCombatComponentFromActor(AActor* InActor, EWarriorValidType& OutValidType);
```

## 

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
        
        ![屏幕截图 2025-04-17 174154.png](UFUNCTION/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-17_174154.png)
        
    

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
    
- Call the function in C++
    
    ```cpp
    HitInterface->Execute_GetHit(BoxHit.GetActor(), BoxHit.ImpactPoint);
    ```
    

## NetMulticast

```cpp
UFUNCTION(NetMulticast, Reliable)
```

- Used to declare a **reliable multicast RPC (Remote Procedure Call)**
- `NetMulticast`:  When the **server** calls this function, it executes **locally on the server** and is **replicated to all connected clients**.
- `Reliable`: The function is **guaranteed to arrive** at its destination, even if network conditions are poor.

## Meta

- TitleProperty
    
    ```cpp
    UPROPERTY(EditDefaultsOnly, BlueprintReadOnly, meta = (TitleProperty = "InputTag"))  
    TArray<FWarriorInputActionConfig> NativeInputActions;
    ```
    

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
    

- BlueprintThreadSafe
    
    ```cpp
    UFUNCTION(BlueprintPure, meta=(BlueprintThreadSafe))
    UWarriorHeroAnimInstance* GetHeroAnimInstance() const;
    ```
    
- Default Value
    
    ```cpp
    UFUNCTION(BlueprintCallable, meta = (ApplyLevel = "1"))
    void GrantHeroWeaponAbilities(int32 ApplyLevel);
    ```
    
- In & Out
    
    ```cpp
    UFUNCTION(BlueprintCallable, Category="Warrior|Ability", meta = (ApplyLevel = "1"))
    void GrantHeroWeaponAbilities(const TArray<FWarriorHeroAbilitySet>& InDefaultWeaponAbilities, int32 ApplyLevel, TArray<FGameplayAbilitySpecHandle>& OutGrantedAbilitySpecHandles);
    ```
    
    ![屏幕截图 2025-05-06 182929.png](UFUNCTION/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-06_182929.png)