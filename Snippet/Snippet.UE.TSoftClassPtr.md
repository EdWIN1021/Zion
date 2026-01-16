[[Concept.UE.TSoftClassPtr]]

```cpp
TSoftClassPtr<AWarriorEnemyCharacter> CachedSoftEnemyClassToSpawn;
```

# IsNull
```cpp
CachedSoftEnemyClassToSpawn.IsNull();
```

## Get
```cpp
UClass* LoadedClass = CachedSoftEnemyClassToSpawn.Get();
```

## ToSoftObjectPath
```cpp
UAssetManager::Get().GetStreamableManager().RequestAsyncLoad(  
    CachedSoftEnemyClassToSpawn.ToSoftObjectPath(),  
    FStreamableDelegate::CreateUObject(this, &ThisClass::OnEnemyClassLoaded)  
);
```