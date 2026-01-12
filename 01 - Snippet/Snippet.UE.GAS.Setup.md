
The Gameplay Ability System is a core component of Unreal Engine for managing abilities and attributes in character-driven games. Below is a concise guide to setting up and using the ability system.

## Debug

```
showdebug abilities
```


## Dependencies

Add these public dependencies to your project's `.Build.cs` file:

```cpp
PublicDependencyModuleNames.AddRange(new string[] { "GameplayAbilities", "GameplayTags", "GameplayTasks" });
```


## Key Components

### Ability System Component

Create a custom `UAbilitySystemComponent` class that inherits from `UAbilitySystemComponent`.

```cpp
class WARRIOR_API UWarriorAbilitySystemComponent : public UAbilitySystemComponent
{
    GENERATED_BODY()
    
    // Add any additional functionality here
};
```

### Attribute Set

Create a custom attribute set class that inherits from `UAttributeSet`.

```cpp
class WARRIOR_API UWarriorAttributeSet : public UAttributeSet
{
    GENERATED_BODY()

    // Define your attributes here
};
```


## Character Setup

In your character class, declare and initialize the ability system component and attribute set:

```cpp
UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = "AbilitySystem")
UWarriorAbilitySystemComponent* WarriorAbilitySystemComponent;

UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = "AbilitySystem")
UWarriorAttributeSet* WarriorAttributeSet;
```

Initialize these components in the constructor:

```cpp
AWarriorBaseCharacter::AWarriorBaseCharacter()
{
    WarriorAbilitySystemComponent = CreateDefaultSubobject<UWarriorAbilitySystemComponent>(TEXT("WarriorAbilitySystemComponent"));
    WarriorAttributeSet = CreateDefaultSubobject<UWarriorAttributeSet>(TEXT("WarriorAttributeSet"));
}
```


## Possession Event

Override the `PossessedBy` function to initialize the ability system:

```cpp
void AWarriorBaseCharacter::PossessedBy(AController* NewController)
{
    Super::PossessedBy(NewController);

    if (WarriorAbilitySystemComponent)
    {
        WarriorAbilitySystemComponent->InitAbilityActorInfo(this, this);
    }
}
```


## Implementing the Ability System Interface

Make your character class implement `IAbilitySystemInterface`:

```cpp
class WARRIOR_API AWarriorBaseCharacter : public ACharacter, public IAbilitySystemInterface
{
    // Your other code here
};
```


## Accessing the Ability System Component

Override the `GetAbilitySystemComponent` function to return your custom component

```cpp
UAbilitySystemComponent* AWarriorBaseCharacter::GetAbilitySystemComponent() const
{
    return GetWarriorAbilitySystemComponent();
}
```



