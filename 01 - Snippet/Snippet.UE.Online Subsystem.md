# Online Subsystem

## Config

- Edit → Plugins
    
    ![Screenshot 2025-01-25 205359.png](Online%20Subsystem/Screenshot_2025-01-25_205359.png)
    
- Build.cs
    
    ```cpp
    PrivateDependencyModuleNames.AddRange(new string[] { "OnlineSubsystem", "OnlineSubSystemSteam" });
    ```
    
- Config → DefaultEngine.ini
    
    ```cpp
    [/Script/Engine.GameEngine]
    +NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="OnlineSubsystemSteam.SteamNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")
    
    [OnlineSubsystem]
    DefaultPlatformService=Steam
    
    [OnlineSubsystemSteam]
    bEnabled=true
    SteamDevAppId=480
    bInitServerOnClient=true
    
    [/Script/OnlineSubsystemSteam.SteamNetDriver]
    NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
    ```
    

[`*IOnlineSubsystem*`](https://www.notion.so/IOnlineSubsystem-1878d590ff3880f2961be1463b15a486?pvs=21) 

[`*IOnlineSession*`](https://www.notion.so/IOnlineSession-1878d590ff3880689b83cd3e25880965?pvs=21) 

[`*FOnlineSessionSettings*`](https://www.notion.so/FOnlineSessionSettings-1888d590ff38806a9aa8f5d12f1d2933?pvs=21) 

[`FOnlineSessionSearch`](https://www.notion.so/FOnlineSessionSearch-1888d590ff3880f1bd51e34e675b4546?pvs=21) 

[`FOnCreateSessionCompleteDelegate`](https://www.notion.so/FOnCreateSessionCompleteDelegate-1878d590ff3880799b96d368144ddfdc?pvs=21) 

[`FOnFindSessionsCompleteDelegate`](https://www.notion.so/FOnFindSessionsCompleteDelegate-1888d590ff3880a19e42e62c27a8fe22?pvs=21)