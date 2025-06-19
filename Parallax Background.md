
![[Screenshot 2025-06-19 153825 1.png]]

### 摄像机在水平方向（X轴）上移动了多少距离，并更新记录的摄像机位置

```csharp
public class PrallaxLayer
{
    [SerializeField] private Transform background;       // 背景物体的 Transform 引用
    [SerializeField] private float parallaxMultiplier;   // 视差移动比例系数

    public void Move(float distanceToMove)
    {
        // 根据摄像机移动距离和视差系数，计算并更新背景位置
        background.position += Vector3.right * (distanceToMove * parallaxMultiplier);
    }
}
```

```cpp
void Update()  
{
	float currentCameraPositionX = mainCamera.transform.position.x;  
	float distanceToMove = currentCameraPositionX - lastCameraPositionX;  
	lastCameraPositionX = currentCameraPositionX;
	
	foreach ( PrallaxLayer layer in backgroundLayers )  
	{  
	    layer.Move(distanceToMove);  
	}
}
```



- 如果 `parallaxMultiplier = 1.0`：  
    背景跟摄像机一起完全同步移动（没视差）。
    
- 如果 `parallaxMultiplier = 0.5`：  
    摄像机移动 10 单位，背景只移动 5 单位，制造出“远处”的感觉。
    
- 如果 `parallaxMultiplier = 0.0`：  
    背景根本不动，看起来是最远的背景。
    
- 如果 `> 1.0`：  
    背景移动比相机快（少见，一般用来制造前景）



