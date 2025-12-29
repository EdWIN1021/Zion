
- 这个 InstancedStruct 只能装载来自模块 Inventory 里的 FInv_ItemManifest 或其子结构体。
- `FInstancedStruct` 是一个“可以在运行时保存任意结构体”的容器。你可以在运行时选择它的结构类型，只要它符合设定的 `BaseStruct` 类型。

```CPP
UPROPERTY(VisibleAnywhere, meta = (BaseStruct = "/Script/Inventory.Inv_ItemManifest"), Replicated)  
FInstancedStruct ItemManifest;
```



```CPP
ItemManifest = FInstancedStruct::Make<FInv_ItemManifest>(Manifest);
```


```CPP
PublicDependencyModuleNames.AddRange(  
    new string[]  
    {       
       "StructUtils"  
    }  
    );
```