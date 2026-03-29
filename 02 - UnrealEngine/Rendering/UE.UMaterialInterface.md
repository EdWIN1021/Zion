- 是材质的 **接口基类**（基底类），它本身不能直接实例化。
- 技能系统、UI 显示系统
- 技能图标材质（可能用到 Material Instance Dynamic）


```cpp
UPROPERTY(EditDefaultsOnly, BlueprintReadOnly)  
TSoftObjectPtr<UMaterialInterface> AbilityIconMaterial;
```