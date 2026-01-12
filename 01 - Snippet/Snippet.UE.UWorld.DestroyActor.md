# DestroyActor

Access Specifier: public
Description: Destroys an actor by removing it from the world and marking it for garbage collection

Marks the actor and all its components to be removed from the world and destroyed.

### Lifecycle

When `DestroyActor` is called:[[1]](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-actor-lifecycle)

1. **EndPlay** phase begins
2. Actor is marked as **pending kill**
3. Actor is removed from the world's actor array
4. Garbage collector removes all references
5. **BeginDestroy** → **IsReadyForFinishDestroy** → **FinishDestroy**

### Usage

```cpp
// Destroy this actor
Destroy();

// Or destroy another actor
ActorToDestroy->Destroy();
```

> **Note:** The actor does not destroy its child actors automatically, only itself and its components.[[2]](https://forums.unrealengine.com/t/how-destroy-actor-works/620200)
>