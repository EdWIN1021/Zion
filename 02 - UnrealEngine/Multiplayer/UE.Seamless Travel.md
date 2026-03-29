# Seamless Travel

## Server Travel

```cpp
UWorld::ServerTravel
```

- Server Only
- Jumps the server to a new level
- All connected clients will follow
- Server calls  `APlayerController:ClientTravel`

## Client Travel

```cpp
APlayerController:ClientTravel
```

- When called from a client: travel to new server
- When called from a server: makes the player travel to a new map

- Create a Game Mode
- Set `Use Seamless Travel` to true
- Create Transition Map (Empty Level)
- Project Settings → Map & Mode → Transition Map