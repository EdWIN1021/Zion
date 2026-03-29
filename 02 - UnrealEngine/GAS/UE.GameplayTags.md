# GameplayTags

Tags: GAS

<aside>

Edit → Project Settings → GameplayTags

</aside>

```cpp
// Build.cs
PublicDependencyModuleNames.AddRange(new string[] { "GameplayTags" });
```

## Header

```cpp
#include "NativeGameplayTags.h"

namespace WarriorGameplayTags
{
    WARRIOR_API UE_DECLARE_GAMEPLAY_TAG_EXTERN(InputTag_Move);
}
```

### CPP

```cpp
namespace WarriorGameplayTags
{
    UE_DEFINE_GAMEPLAY_TAG(InputTag_Move, "InputTag.Move");
}
```