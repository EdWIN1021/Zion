```
Window -> Package Manager -> Unity Registry -> Cinemachine

Cinemachine -> Targeted Camera -> 2D Camera
```

---

### MainCamera
- Update Method: Fixed Update


Use `FixedUpdate()` for the Main Camera **only if it is following a physics object** (like a `Rigidbody`) to ensure smoother, consistent movement that matches Unity’s physics engine.

```csharp
void FixedUpdate()  
{  

}
```

---
### CinemachineCamera

#### Cinemachine Camera

- Tracking Target: [[#Player]]
- Lens
- Add Extension: [[#Cinemachine Confiner 2D]]

#### Cinemachine Position Composer

- Camera Distance
- Screen Position
- Dead Zone
- Hard Limits
- Center On Activate
- Target Offset
- Damping
- Lookhead

#### Cinemachine Confiner 2D

- Bounding Shape 2D: [[#CinemachineConfiner]]

---

### CinemachineConfiner

#### Polygon Collider 2D
- IsTrigger: true  
- Points

---
### Player
- Interpolate: None