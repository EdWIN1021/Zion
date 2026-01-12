# UGameplayAbility

Base: UObject (UObject%201378d590ff3880b19696d9852e8a88d8.md) 
System: GAS
Type: Class

```cpp
' + num pad 3
```

[@UGameplayAbility ](UGameplayAbility/@UGameplayAbility%2013d8d590ff38806e9cceda8d8b57ea3b.csv)

[@UObject ](UObject/@UObject%2013b8d590ff388024a9aafc1d1fda1d21.csv)

## Blueprint

- Instancing Policy
    - The ability is instantiated **once per actor**, and this instance is reused every time the ability is activated
- Instanced Per Execution
    - A new instance of the ability is created every time it is activated

- Ability Triggers (Ability is activated by sent gameplay event to owning actor function)
    - Trigger Tag: Event.HitReact
    - Trigger Source: Gameplay Event
        
        ![屏幕截图 2025-05-09 180353.png](UGameplayAbility/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-09_180353.png)