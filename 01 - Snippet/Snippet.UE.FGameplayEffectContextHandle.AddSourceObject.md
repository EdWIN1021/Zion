# AddSourceObject

<aside>

Sets the object this effect was created from

</aside>

```cpp
/** Sets the object this effect was created from. */
virtual void AddSourceObject(const UObject* NewSourceObject)
{
	SourceObject = MakeWeakObjectPtr(const_cast<UObject*>(NewSourceObject));
	bReplicateSourceObject = NewSourceObject && NewSourceObject->IsSupportedForNetworking();
}
```

```cpp
EffectContextHandle.AddSourceObject(Projectile);
```