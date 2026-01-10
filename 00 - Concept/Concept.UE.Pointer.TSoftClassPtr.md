它是一种不会立即加载资源、只在需要时才加载的智能引用，适合延迟加载类（比如蓝图类）

```cpp
TSoftClassPtr<AWarriorEnemyCharacter> CachedSoftEnemyClassToSpawn;
```

## IsNull
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