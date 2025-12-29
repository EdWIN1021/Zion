

## Setting Up the Module
```cpp
		PublicDependencyModuleNames.AddRange(new string[] { "GameplayTags" });
```
        
## Creating a Custom GameplayTag Class
- Create a new C++ class named `WarriorGameplayTags` that will hold your custom tags.
- Include the `NativeGameplayTags.h` header file to access the necessary macros and functions.

```CPP
#include "NativeGameplayTags.h"
```

 ## Declaring Tags in Header File

---
		
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