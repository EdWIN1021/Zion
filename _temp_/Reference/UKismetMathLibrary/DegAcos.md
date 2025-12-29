```cpp
const float DotResult = FVector::DotProduct(VictimForward, VictimToAttackerNormalized);  
OutAngleDifference = UKismetMathLibrary::DegAcos(DotResult);
```
