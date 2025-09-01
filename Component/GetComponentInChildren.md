---
member: function
Class: "[[Component]]"
---


`true` 表示在查找子物体组件时 **包含未激活（Inactive）的 GameObject**。

```cpp
 skillTree = GetComponentInChildren<UI_SkillTree>(true);
```