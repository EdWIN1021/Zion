# ServerTravel

Access Specifier: public
Description: The  function is used in Unreal Engine to initiate a server-side map travel. This means that the server will load the specified map, and all connected clients will follow the server to the new map.

## Config

![Screenshot 2025-01-31 112020.png](ServerTravel/Screenshot_2025-01-31_112020.png)

## **Declaration**

```cpp
	bool ServerTravel(const FString& InURL, bool bAbsolute = false, bool bShouldSkipGameNotify = false);
```

## **Example**

```cpp
UWorld* World = GetWorld();
if (World)
{
	World->ServerTravel("/Game/Maps/Lobby");
}
```