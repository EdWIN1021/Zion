# Play Animation Montage in Gameplay Ability

Tags: GAS

![屏幕截图 2025-05-06 000500.png](Play%20Animation%20Montage%20in%20Gameplay%20Ability/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-06_000500.png)

To set up an animation montage with synchronized events in your Ability Blueprint, follow these steps:

1. **Play Montage**: Use `PlayMontageAndWait` to initiate the animation and pause execution until it completes.
2. **Create AnimNotify Event**:
    
    ![屏幕截图 2025-05-06 000933.png](Play%20Animation%20Montage%20in%20Gameplay%20Ability/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-05-06_000933.png)
    
    - Make a new Blueprint Function that sends an event tag when triggered by an animation notify.
3. **Integrate AnimNotify in Animation**:
    - Open your animation montage.
    - Insert an `AnimNotify` at the desired frame to trigger the event.
4. **Assign Event Tag**:
    - In the AnimNotify node, set the `EventTag` parameter to a unique identifier for your event.
5. **Wait for Event in Ability**:
    - After `PlayMontageAndWait`, add `WaitGameplayEvent`.
    - Set its `EventTag` to match the one defined in your AnimNotify.

This setup ensures that when the animation reaches the notify point, it triggers the event, which the Ability Blueprint is waiting on. This allows for seamless synchronization between animation and gameplay logic.