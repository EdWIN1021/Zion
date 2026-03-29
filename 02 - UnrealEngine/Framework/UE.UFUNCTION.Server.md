- 只有 **客户端**  可以调用它，执行会发生在 **服务器端**

```cpp
UFUNCTION(Server, Reliable)  
void Server_AddNewItem(UInv_ItemComponent* ItemComponent, int32 StackCount);
```


```cpp
void UInv_InventoryComponent::Server_AddNewItem_Implementation(UInv_ItemComponent* ItemComponent, int32 StackCount)  
{  
    UInv_InventoryItem* NewItem = InventoryList.AddEntry(ItemComponent);  
}
```