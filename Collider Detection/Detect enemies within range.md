```cpp
public Collider2D[] targetColliders;

[SerializeField] private Transform targetCheck;  
[SerializeField] private float targetCheckRadius = 1;  
[SerializeField] private LayerMask whatIsTarget;

targetColliders = Physics2D.OverlapCircleAll(targetCheck.position, targetCheckRadius, whatIsTarget);
```