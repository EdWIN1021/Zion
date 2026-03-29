## Enabling MetaSound and Creating Your Source Asset

1. Enable the MetaSound plugin
    - In the Editor, go to **Edit → Plugins**, search for **MetaSound**, and enable it. Restart the Editor.
2. Create a MetaSound Source
    - In the Content Browser, click **Add → Audio → MetaSound Source** and name it.

![[Assets/UnrealEngine/UE.MetaSound.Mono_02.png | center]]

![[Assets/UnrealEngine/UE.MetaSound.Mono_03.png | center]]
## Playing MetaSounds in C++

```cpp
UGameplayStatics::PlaySoundAtLocation( this, EquipSound, GetActorLocation() );
```

![[Assets/UnrealEngine/UE.MetaSound.Mono_01.png]]