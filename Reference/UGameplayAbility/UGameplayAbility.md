---
Category: Class
---
**Activation Owned Tags** are `GameplayTags` added to an ability's owner (e.g., a character) **when the ability is activated** and automatically removed when the ability **ends or is canceled**.



Instancing Policy: 

|                             |                                         |                    |           |
| --------------------------- | --------------------------------------- | ------------------ | --------- |
| **`NonInstanced`**          | 不创建独立实例，所有执行共享同一个 `UGameplayAbility` 对象 | 简单瞬时技能（如普攻）        | ✅ 内存占用最低  |
| **`InstancedPerActor`**     | 每个**角色**创建唯一实例，能力激活期间复用同一实例             | 冷却技能、可持续状态（如格挡）    | ⚠️ 中等内存占用 |
| **`InstancedPerExecution`** | 每次**激活**都创建新实例，结束后销毁                    | 需独立状态的能力（如蓄力、通道技能） |           |
