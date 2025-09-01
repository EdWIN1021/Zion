![[Untitled 1.base]]



```cpp
[SerializeField] private Image skillIcon;
```
### Raycast Target
- The `Raycast Target` property in Unity determines whether a UI element can be detected by user input events like clicks and touches.
- It will **block** the ray, preventing UI elements located behind it from being hit.




### Image Type
- Simple
- Sliced (4 个角：不会被拉伸，保持原始大小, 4 条边：只会横向或纵向拉伸, 中间区域：可以自由拉伸填充)