# Setup Animation Blueprint

Tags: Animation

<aside>

- Animation → Animation Blueprint
- New C++ Class → AnimInstance
</aside>

| Blueprint | C++ |
| --- | --- |
| Event Blueprint Initialize Animation | [`*NativeInitializeAnimation*`](https://www.notion.so/NativeInitializeAnimation-18d8d590ff38809b95a9c6a03d119f0a?pvs=21)  |
| Event Blueprint Update Animation | [`*NativeUpdateAnimation*`](https://www.notion.so/NativeUpdateAnimation-18d8d590ff3880b499f4c8313d41bce9?pvs=21)  |
- Ground Speed
    
    ```cpp
    GroundSpeed = UKismetMathLibrary::VSizeXY(SlashCharacterMovement->Velocity);
    ```
    
    ![屏幕截图 2025-04-10 225356.png](Setup%20Animation%20Blueprint/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-10_225356.png)
    
- Jumping
    
    ```cpp
    IsFalling = SlashCharacterMovement->IsFalling();
    ```