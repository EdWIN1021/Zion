```cpp
/* 异步加载 CachedSoftEnemyClassToSpawn 软引用指向的资源，加载完成后调用 OnEnemyClassLoaded */

UAssetManager::Get().GetStreamableManager().RequestAsyncLoad(  
		CachedSoftEnemyClassToSpawn.ToSoftObjectPath(),  
		FStreamableDelegate::CreateUObject(this, &ThisClass::OnEnemyClassLoaded)  
);
```