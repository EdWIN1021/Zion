# Gameplay Ability Implementation

Tags: GAS

**1. Create the C++ Gameplay Ability Class:**

- **Navigate:** In your Unreal Engine project, go to your project's Content Browser. Locate the `Content/Code` folder or your preferred directory for C++ classes.
- **Create New C++ Class:** Right-click within the folder and select **C++ Class**.
- **Parent Class:** In the "Create C++ Class" wizard, select **GameplayAbility** as the parent class.
- **Name the Class:** Name your new class `UWarriorGameplayAbility`. It's good practice to prefix custom Gameplay Ability classes with `U`.
- **Create Class Files:** Click "Create Class" to generate the `UWarriorGameplayAbility.h` and `UWarriorGameplayAbility.cpp` files.

**2. Override the `OnGiveAbility` Function:**

- **Purpose:** The `OnGiveAbility` function is called by the Ability System Component (ASC) when this ability is granted to an Actor. Overriding it allows you to execute custom logic at the moment the ability is given.
- **Implementation (`UWarriorGameplayAbility.cpp`):**C++
    
    ```cpp
    #include "WarriorGameplayAbility.h"
    #include "AbilitySystemComponent.h"
    
    void UWarriorGameplayAbility::OnGiveAbility(const FGameplayAbilityActorInfo* ActorInfo, const FGameplayAbilitySpec& Spec)
    {
        Super::OnGiveAbility(ActorInfo, Spec);
    
        // Optional: Automatically activate the ability upon being granted.
        // This can be useful for passive abilities or abilities that should start immediately.
        if (ActorInfo && !Spec.IsActive())
        {
            ActorInfo->AbilitySystemComponent->TryActivateAbility(Spec.Handle);
        }
    }
    ```
    
- **Explanation:**
    - `Super::OnGiveAbility(ActorInfo, Spec);`: It's crucial to call the parent class's implementation to ensure default functionality is executed.
    - `ActorInfo`: Provides information about the Actor possessing the ability (e.g., the Ability System Component).
    - `Spec`: Contains details about how the ability was granted, including its handle (unique identifier) and level.
    - `TryActivateAbility`: This line attempts to activate the ability immediately after it's granted, but only if it's not already active.

**3. Override the `EndAbility` Function:**

- **Purpose:** The `EndAbility` function is called when the ability instance is ending, either through normal completion, cancellation, or other means. This is the place to perform any necessary cleanup.
- **Implementation (`UWarriorGameplayAbility.cpp`):**C++
    
    ```cpp
    #include "AbilitySystemComponent.h"
    
    void UWarriorGameplayAbility::EndAbility(const FGameplayAbilitySpecHandle Handle, const FGameplayAbilityActorInfo* ActorInfo, const FGameplayAbilityActivationInfo ActivationInfo, bool bReplicateEndAbility, bool bWasCancelled)
    {
        Super::EndAbility(Handle, ActorInfo, ActivationInfo, bReplicateEndAbility, bWasCancelled);
    
        // Optional: Clear the ability from the AbilitySystemComponent when it ends.
        // Be cautious with this; it might not always be the desired behavior.
        // For example, you might want a passive ability to remain granted.
        if (ActorInfo && ActorInfo->AbilitySystemComponent.IsValid())
        {
            ActorInfo->AbilitySystemComponent->ClearAbility(Handle);
        }
    }
    ```
    
- **Explanation:**
    - `Super::EndAbility(...)`: Again, calling the parent's implementation is important.
    - `Handle`: The unique identifier of the specific ability instance that is ending.
    - `ActivationInfo`: Contains information about how the ability was activated.
    - `bReplicateEndAbility`: Indicates if the ability end should be replicated to clients.
    - `bWasCancelled`: True if the ability was ended due to cancellation.
    - `ClearAbility`: This function removes the ability from the ASC. **Use this with caution**, as it might not be appropriate for all ability types. Consider if you want the ability to be re-activatable later.

**4. Create a Blueprint Class for Designer Use:**

- **Purpose:** Creating a Blueprint child class of your C++ ability allows designers to easily create variations of the ability, set properties, and integrate it into gameplay without needing to write C++ code.
- **Steps:**
    1. **Navigate:** In the Content Browser, go to the folder where you want to create the Blueprint (e.g., `Content/Blueprints/Abilities`).
    2. **Create Blueprint Class:** Right-click and select **Blueprint Class**.
    3. **Parent Class:** In the "Pick Parent Class" window, search for and select your `WarriorGameplayAbility` (it might appear as "Warrior Gameplay Ability" in the editor).
    4. **Name the Blueprint:** Name it `BP_WarriorGameplayAbility`.
- **Benefits:** Designers can now:
    - Modify properties exposed in your C++ class (if you add `UPROPERTY(EditDefaultsOnly)` or `UPROPERTY(EditAnywhere)`).
    - Add Blueprint logic within the ability's execution flow (using event graphs if you override BlueprintCallable functions in C++).
    - Easily create multiple variations of the warrior ability with different parameters.

**5. Granting Abilities to Characters:**

- **Prerequisites:** Ensure your character class (e.g., `AWarriorCharacter`) has:
    - An instance of a `UAbilitySystemComponent`. This is typically added as a component to your character in either C++ or Blueprint.
    - A way to access this component (e.g., a public getter function: `GetAbilitySystemComponent()`).
- **Steps to Grant the Ability (Example within `AWarriorCharacter::InitializeAbilities()`):**C++
    
    ```cpp
    #include "WarriorCharacter.h"
    #include "AbilitySystemComponent.h"
    #include "WarriorGameplayAbility.h" // Include your custom ability header
    #include "GameplayAbilitySpec.h"
    #include "GameplayTag.h" // Include for Gameplay Tags
    
    void AWarriorCharacter::InitializeAbilities()
    {
        // Ensure the Ability System Component is valid
        if (UAbilitySystemComponent* ASC = GetAbilitySystemComponent())
        {
            // Create an ability specification for the warrior's attack ability
            FGameplayAbilitySpec AttackSpec(NewObject<UWarriorGameplayAbility>(this), 1, INDEX_NONE, this);
            // Arguments:
            // 1. Ability: The Gameplay Ability object to grant. We create a new object here.
            // 2. Level: The initial level of the ability.
            // 3. InputID: The input binding for this ability (can be INDEX_NONE if not input-driven).
            // 4. SourceObject: The object granting the ability (usually the character).
    
            // Optional: Add Gameplay Tags to the ability specification.
            // This allows for more flexible ability management and targeting.
            FGameplayTag AbilityTag = FGameplayTag::RequestGameplayTag(FName("Ability.Warrior.Attack"));
            AttackSpec.DynamicAbilityTags.AddTag(AbilityTag);
    
            // Grant the ability to the character
            ASC->GiveAbility(AttackSpec);
    
            // Optional: Activate the ability immediately if needed (you might not want to do this here
            // if it's an input-driven ability).
            // ASC->TryActivateAbility(AttackSpec.Handle);
        }
    }
    ```
    
- **Explanation:**
    - `GetAbilitySystemComponent()`: Accesses the character's Ability System Component.
    - `FGameplayAbilitySpec`: A structure that holds information about the ability being granted.
        - The constructor takes the ability object (created using `NewObject`), the initial level, an input ID (if applicable), and the source object.
    - `DynamicAbilityTags`: Allows you to associate Gameplay Tags with this specific instance of the granted ability. This is very useful for filtering, blocking, and triggering other gameplay effects.
    - `ASC->GiveAbility(AttackSpec)`: This crucial function grants the ability to the character, adding it to the ASC's list of available abilities. The `GiveAbility` function returns an `FGameplayAbilitySpecHandle`, which can be used to reference this specific granted ability later.

**Key Improvements and Best Practices:**

- **Include Headers:** Ensure you include the necessary header files in your C++ classes (`#include ...`).
- **Validity Checks:** Always check if pointers (like `ActorInfo` and the result of `GetAbilitySystemComponent()`) are valid before using them.
- **Clear Comments:** Add comments to explain the purpose of your code.
- **`Super::` Calls:** Remember to call the `Super::` implementation of overridden functions.
- **Blueprint Child Class:** Creating a Blueprint child is highly recommended for designer flexibility.
- **Gameplay Tags:** Utilize Gameplay Tags extensively for categorizing abilities, triggering effects, and creating complex gameplay interactions.
- **Careful Use of `ClearAbility`:** Understand the implications of clearing an ability. It might prevent the ability from being used again unless explicitly granted again.
- **Ability Activation:** The `TryActivateAbility` call in `OnGiveAbility` is optional. Decide if you want the ability to activate immediately upon being granted. For input-driven abilities, you'll typically activate them in response to player input.
- **Ability Specification Arguments:** Understand the parameters of the `FGameplayAbilitySpec` constructor.