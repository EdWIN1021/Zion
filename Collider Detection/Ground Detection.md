
```cpp
[SerializeField] private float groundCheckDistance;  
[SerializeField] private LayerMask whatIsGround;  
public bool groundDetected;
```

```cpp
private void HandleCollisionDetection()  
{  
    groundDetected = Physics2D.Raycast(transform.position, Vector2.down, groundCheckDistance, whatIsGround);  
}
```


### Assign Ground Layer in Unity Editor

![[Screenshot 2025-06-19 150720.png]]