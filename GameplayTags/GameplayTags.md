GameplayTags in Unreal Engine are a powerful metadata system used to categorize and manage various aspects of your game, such as mechanics, features, and input actions. They allow you to tag different elements in your game (like actors, components, or events) with specific tags that can be queried or checked at runtime to influence gameplay behavior.

Here's how you can effectively use GameplayTags in your C++ project:

1. **Setting Up the Module:**
    
    - Open your project's `Build.cs` file.
    - Add `"GameplayTags"` to the list of public dependencies:
        
        ```cpp
        PublicDependencyModuleNames.AddRange(new string[] { "GameplayTags" });
        ```
        
    - This includes the necessary GameplayTags functionality in your project.
2. **Creating a Custom GameplayTag Class:**
    
    - Create a new C++ class named `WarriorGameplayTags` that will hold your custom tags.
    - Include the `NativeGameplayTags.h` header file to access the necessary macros and functions.
3. **Declaring Tags in Header File:**
    
    - In the header file (`WarriorGameplayTags.h`), declare your gameplay tags using `UE_DECLARE_GAMEPLAY_TAG_EXTERN`. For example:
        
        ```cpp
        namespace WarriorGameplayTags  
        {  
            /** Input Tags **/  
            WARRIOR_API UE_DECLARE_GAMEPLAY_TAG_EXTERN(InputTag_Move);  
        }
        ```
        
    - This declares a tag named "InputTag.Move".
4. **Defining Tags in CPP File:**
    
    - In the corresponding `.cpp` file (`WarriorGameplayTags.cpp`), define your tags using `UE_DEFINE_GAMEPLAY_TAG`. For example:
        
        ```cpp
        namespace WarriorGameplayTags  
        {  
            /** Input Tags **/  
            UE_DEFINE_GAMEPLAY_TAG(InputTag_Move, "InputTag.Move");  
        }
        ```
        
    - This associates the tag name with its string identifier.


```cpp
WarriorGameplayTags::InputTag_Move
```