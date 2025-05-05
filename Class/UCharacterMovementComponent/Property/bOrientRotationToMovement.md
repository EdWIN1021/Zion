---
Type: bool
tags:
---

When bOrientRotationToMovement is set to true, the character will rotate its orientation (view or body) to face the direction it is moving. This makes movements appear more natural and responsive.

```cpp
GetCharacterMovement()->bOrientRotationToMovement = true;
```