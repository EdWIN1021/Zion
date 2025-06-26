
### Header
用于在 **Inspector（检视器）** 中为字段分组加上标题，提升可读性和组织性

```cpp
[Header("Movement details")] 
public float idleTime = 2;  
public float moveSpeed = 1.4f;
```

### Range

快速限制一个变量的值范围

```cpp
[Range(0, 2)]  // 其值只能在 0 到 2 之间调整
public float moveAnimSpeedMultiplier = 1;
```