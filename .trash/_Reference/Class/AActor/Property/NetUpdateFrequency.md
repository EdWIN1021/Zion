---
Type: float
tags:
---
`NetUpdateFrequency` is a property in Unreal Engine that determines how frequently an Actor (in games) sends state updates over the network. This setting impacts both performance and bandwidth usage.

## Properties:

- **Data Type**: `float`
- **Default Value**: `100.f` (equivalent to 100 milliseconds)
- **Category**: Replication

### Usage

```cpp
UPROPERTY(Category=Replication, EditDefaultsOnly, BlueprintReadWrite)
float NetUpdateFrequency;
```

### Example Initialization:

```cpp
NetUpdateFrequency = 100.f;
```

## Key Considerations

- Lower values result in more frequent updates but higher bandwidth usage.
- Higher values reduce network traffic but may lead to less responsive state changes.
- This setting is particularly important for Actors that have frequently changing states.

## Related Concepts

- **Replication**: The process of synchronizing game state across multiple clients.
- **Network Latency**: Affects how timely updates are received by