# UGameplayAbility
```cpp
' + num pad 3
```

## Blueprint

- Instancing Policy
    - The ability is instantiated **once per actor**, and this instance is reused every time the ability is activated

- Instanced Per Execution
    - A new instance of the ability is created every time it is activated

- Ability Triggers (Ability is activated by sent gameplay event to owning actor function)
    - Trigger Tag: Event.HitReact
    - Trigger Source: Gameplay Event
