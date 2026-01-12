# SetViewTarget

Access Specifier: public
Category: Function
Description: Its job is to switch the active camera for a player

```cpp
	TArray<AActor*> FoundCameras;
	UGameplayStatics::GetAllActorsOfClassWithTag(this, ACameraActor::StaticClass(), FName("Default"),FoundCameras);

	if (!FoundCameras.IsEmpty())
	{
		/* Its job is to switch the active camera for a player */
		SetViewTarget(FoundCameras[0]); 
	}
```