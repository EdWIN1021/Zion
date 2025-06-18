
### 2D

```csharp
private RigidBody2D rb;
private float moveX;
private float moveSpeed = 10f;

void Start()
{
	rb = GetComponent<RigidBody2D>();
}

void Update() 
{
	moveX = Input.GetAxis("Horizontal");
	rb.linearVelocity = new Vector2(moveX * moveSpeed, rb.linearVelocity.y);
}

```