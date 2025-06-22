### MainCamera
- Update Method: Fixed Update


Use `FixedUpdate()` for the Main Camera **only if it is following a physics object** (like a `Rigidbody`) to ensure smoother, consistent movement that matches Unity’s physics engine.

```csharp
void FixedUpdate()  
{  

}
```


### Player
- Interpolate: None