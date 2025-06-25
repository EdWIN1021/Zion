```cpp title:header
/* 当在编辑器里通过属性面板（Details Panel）修改了某个 UPROPERTY 变量时，这个函数会被自动调用 */
#if WITH_EDITOR  
		virtual void PostEditChangeProperty(struct FPropertyChangedEvent& PropertyChangedEvent) override;  
#endif
```


```cpp title:cpp
#if WITH_EDITOR  
void AWarriorEnemyCharacter::PostEditChangeProperty(struct FPropertyChangedEvent& PropertyChangedEvent)  
{  
    Super::PostEditChangeProperty(PropertyChangedEvent);  

		if (PropertyChangedEvent.GetMemberPropertyName() == GET_MEMBER_NAME_CHECKED(ThisClass, LeftHandCollisionBoxAttachBoneName))  
		{  
		    
		}  
}  
#endif
```