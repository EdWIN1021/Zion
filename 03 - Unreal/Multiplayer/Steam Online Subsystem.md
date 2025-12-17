## Plugins


![[Screenshot 2025-12-16 201508.png | center]]

![[Screenshot 2025-12-16 201539.png | center]]

## DefaultEngine.ini

```
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

## Steam 

Steam Settings -> Downloads -> Download region (US-Dallas)


