Assets/Animation: Create -> Animation -> Animator Controller

```csharp
public Animator animator;
private int moveChangeAni;


private void Awake() 
{
	animator = GetComponentInChildren<Animator>();
}


private Update(){

	if (moveX > 0)  
	{  
	    moveChangeAni = 1;  
	}  
	else if(moveX < 0)  
	{  
	    moveChangeAni = -1;  
	}  
	else  
	{  
	    moveChangeAni = 0;  
	} 
	
	/* This sets an integer parameter named "movement" in the Animator Controller to the value stored in moveChangeAni */
	animator.SetInteger("movement", moveChangeAni);
}

```