```cpp
[SerializeField] private GameObject hitVfx;
```

```cpp
public void CreateOnHitVFX(Transform target)  
{  

	// Quaternion.identity：表示旋转为默认值（无旋转）。
    Instantiate(hitVfx, target.position, Quaternion.identity);  
}
```