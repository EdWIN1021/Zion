# GetStaticMagnitudeIfPossible

<aside>

Returns the magnitude as it was entered in data. Only applies to ScalableFloat or any other type that can return data without context

</aside>

```cpp
bool GetStaticMagnitudeIfPossible(float InLevel, float& OutMagnitude, const FString* ContextString = nullptr) const;
```