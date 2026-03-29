# AddInstigator

<aside>

Sets the instigator and effect causer. Instigator is who owns the ability that spawned this, EffectCauser is the actor that is the physical source of the effect, such as a weapon. They can be the same.

</aside>

```cpp
virtual void AddInstigator(class AActor *InInstigator, class AActor *InEffectCauser);
```

```cpp
EffectContextHandle.AddInstigator(PlayerCharacter, FireballProjectile);
```