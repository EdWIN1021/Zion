# Gameplay Cue

<aside>
💡

In Unreal Engine, a **Gameplay Cue** is part of the **Gameplay Ability System (GAS)** and is used to handle visual or audio effects associated with gameplay events, such as playing particle effects, sounds, or animations when a specific ability or gameplay effect is applied.

</aside>

Create a Gameplay Cue asset base on `GameplayCueNotify_Static`

Create a Gameplay Tag for the Cue

Override `OnExecute`

![屏幕截图 2025-05-10 185315.png](Gameplay%20Cue/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-10_185315.png)

 

Call `ExecuteGameplayCue OnOwner`

![屏幕截图 2025-05-10 185336.png](Gameplay%20Cue/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-10_185336.png)

config → DefaultGame.ini

```cpp
GameplayCueNotifyPaths = "/Game/GameplayCues"
```