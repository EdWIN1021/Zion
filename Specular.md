高光反射的光斑强烈成都取决于观察方向与反射方向的夹角大小 

角度越大值越小，角度越小值越大

![[Screenshot 2025-06-18 220806.png]]

```cpp
lightDir = reflect(lightDir, normal)
specular = max(dot(lightRef, -viewDir), 0.0)
```