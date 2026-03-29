## Plugins


![[Assets/UnrealEngine/UE.Multiplayer.Steam Online_01.png | center]]

![[Assets/UnrealEngine/UE.Multiplayer.Steam Online_02.png | center]]

## DefaultEngine.ini

```ini
[/Script/Engine.GameEngine]
!NetDriverDefinitions=ClearArray
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="/Script/SteamSockets.SteamSocketsNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")

[OnlineSubsystem]
DefaultPlatformService=Steam

[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480

;if using Sessions
bInitServerOnCline=true

[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
```

## Build.cs

```c#
		PublicDependencyModuleNames.AddRange(new string[] {
			"OnlineSubsystem",
			"OnlineSubsystemSteam"
		});
```

## Steam 

Steam Settings -> Downloads -> Download region (US-Dallas)


