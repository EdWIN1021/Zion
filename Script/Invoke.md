Invoke allows you to call a method after a specified delay

```cpp
 public void SetupShard(float destinationTime)
 {
     Invoke(nameof(Explode), destinationTime);
 }
```