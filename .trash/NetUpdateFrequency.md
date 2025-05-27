---
Category: Property
---

> [!tip]
> NetUpdateFrequency is a property in Unreal Engine that determines how frequently an Actor (in games) sends state updates over the network. This setting impacts both performance and bandwidth usage.


```cpp title:header
UPROPERTY(Category=Replication, EditDefaultsOnly, BlueprintReadWrite) 
float NetUpdateFrequency;
```

```cpp title:cpp
NetUpdateFrequency = 100.f;
```

