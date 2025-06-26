
### GetComponent

```csharp
private RigidBody2D rb;

void Start()
{
	rb = GetComponent<Rigidbody2D>();
}
```



### GetComponentInChildren

```cpp
public Animator animator;

private void Awake() 
{
	animator = GetComponentInChildren<Animator>();
}

```


### GetComponentInParent
```cpp
private void Awake()  
{  
    entity = GetComponentInParent<Entity>();  
}
```