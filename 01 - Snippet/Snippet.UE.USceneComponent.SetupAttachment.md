# SetupAttachment

Access Specifier: public
Description: Initializes desired Attach Parent and SocketName to be attached to when the component is registered.

## **Declaration**

```cpp
	/** 
	* Initializes desired Attach Parent and SocketName to be attached to when the component is registered.
	* Generally intended to be called from its Owning Actor's constructor and should be preferred over AttachToComponent when
	* a component is not registered.
	* @param  InParent				Parent to attach to.
	* @param  InSocketName			Optional socket to attach to on the parent.
	*/
	ENGINE_API void SetupAttachment(USceneComponent* InParent, FName InSocketName = NAME_None);
```

## **Example**

```cpp
HealthBar->SetupAttachment(GetRootComponent());
FollowCamera->SetupAttachment(CameraBoom, USpringArmComponent::SocketName);
```