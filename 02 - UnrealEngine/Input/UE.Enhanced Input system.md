# Enhanced Input system

1.  Create an Input Mapping Context
2. Create Input Actions
3. Declare Input Mapping Context & Actions in C++
    
    ```cpp
    UPROPERTY(EditAnywhere, Category = "Input")
    TObjectPtr<UInputMappingContext> MappingContext;
    
    UPROPERTY(EditAnywhere, Category = "Input")
    TObjectPtr<UInputAction> MoveAction;
    ```
    
4. Initialize Enhanced Input Local Player Subsystem
    
    ```cpp
    	UEnhancedInputLocalPlayerSubsystem* Subsystem = ULocalPlayer::GetSubsystem<UEnhancedInputLocalPlayerSubsystem>(GetLocalPlayer());
    	Subsystem->AddMappingContext(AuraContext, 0);
    ```
    
5. Create Callback functions
6. Bind Actions with Callback functions
    
    ```cpp
    	UAuraInputComponent* AuraInputComponent = CastChecked<UAuraInputComponent>(InputComponent);
    	AuraInputComponent->BindAction(MoveAction, ETriggerEvent::Triggered, this, &AAuraPlayerController::Move);
    ```
    
7. Assign Mapping Context and Input Actions in Blueprint

[**UInputMappingContext**](https://www.notion.so/UInputMappingContext-18d8d590ff38805a9fe9ecfc9d1b3743?pvs=21) 

[**UInputAction**](https://www.notion.so/UInputAction-18d8d590ff388045861ced756b3b6060?pvs=21)