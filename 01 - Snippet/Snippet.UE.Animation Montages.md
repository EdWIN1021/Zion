# Animation Montages

Tags: Animation

### Create Slot in AnimGraph

![屏幕截图 2025-04-13 014021.png](Animation%20Montages/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-13_014021.png)

### Play Montage

- Blueprint
    
    ![屏幕截图 2025-04-13 022149.png](Animation%20Montages/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-13_022149.png)
    
- C++
    - Create [**UAnimMontage**](https://www.notion.so/UAnimMontage-1898d590ff3880ec897ac405a1efb19a?pvs=21) Pointer
    - Get [**UAnimInstance**](https://www.notion.so/UAnimInstance-1898d590ff38800e8480c03a72091b18?pvs=21) from Mesh
        
        ```cpp
        UAnimInstance* AnimInstance =  GetMesh()->GetAnimInstance();
        ```
        
    - Play Montage
        
        ```cpp
        	UAnimInstance* AnimInstance =  GetMesh()->GetAnimInstance();
        	if (AnimInstance && AttackMontage)
        	{
        		AnimInstance->Montage_Play(AttackMontage);
        	}
        ```
        
    - Jump to Section
        
        ```cpp
        UAnimInstance* AnimInstance =  GetMesh()->GetAnimInstance();
        	if (AnimInstance && AttackMontage)
        	{
        		AnimInstance->Montage_Play(AttackMontage);
        		int32 Selection = FMath::RandRange(0, 1);
        		FName SelectionName = FName();
        		switch (Selection)
        		{
        			case 0:
        				SelectionName = FName("Attack1");
        				break;
        			case 1:
        				SelectionName = FName("Attack2");
        				break;
        			default:
        				break;
        		}
        		AnimInstance->Montage_JumpToSection(SelectionName, AttackMontage);
        	}
        ```