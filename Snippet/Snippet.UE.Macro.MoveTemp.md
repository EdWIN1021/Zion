
MoveTemp in Unreal Engine is like std::move, telling the compiler to transfer resources from one object to another instead of copying them.


```cpp
FInv_SlotAvailabilityResult Result;  
Result.TotalRoomToFill = 1;  
  
FInv_SlotAvailability SlotAvailability;  
SlotAvailability.AmountToFill = 1;  
SlotAvailability.Index = 0;  
  
Result.SlotAvailabilities.Add(MoveTemp(SlotAvailability));
```