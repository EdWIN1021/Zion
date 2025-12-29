---
Category: Function
---

> [!NOTE]
> Destroy this actor. Returns true the actor is destroyed or already marked for destruction, false if indestructible

```cpp
 ENGINE_API bool Destroy(bool bNetForce = false, bool bShouldModifyLevel = true );
```

```cpp
// server-side function by default 
Destroy();
```