## Enabling MetaSound and Creating Your Source Asset

1. Enable the MetaSound plugin
    - In the Editor, go to **Edit → Plugins**, search for **MetaSound**, and enable it. Restart the Editor.
2. Create a MetaSound Source
    - In the Content Browser, click **Add → Audio → MetaSound Source** and name it.

![[Screenshot 2025-12-20 124144.png | center]]

![[Screenshot 2025-12-20 124830.png | center]]
## Playing MetaSounds in C++

```cpp
UGameplayStatics::PlaySoundAtLocation( this, EquipSound, GetActorLocation() );
```

![[Screenshot  2025-04-14 190251.png]]