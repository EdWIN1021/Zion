# [[AActor]]

## Server

- Spawned on server
- Has Authority

```cpp
ENetRole::ROLE_Authority
```

## Client

- Spawned on Client
- Does not have Authority

```cpp
ENetRole::ROLE_AutonomousProxy
```

## Other Clients

```cpp
ENetRole::ROLE_SimulatedProxy
```