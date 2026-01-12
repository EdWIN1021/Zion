# Destroy-

Category: Function
Description: Destroy this actor. Returns true the actor is destroyed or already marked for destruction, false if indestructible

## **Declaration**

```cpp
 
ENGINE_API bool Destroy(bool bNetForce = false, bool bShouldModifyLevel = true );
```

## **Example**

```cpp
// server-side function by default
Destroy();
```