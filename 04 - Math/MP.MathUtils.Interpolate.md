> [!NOTE]
> To estimate or calculate a value that lies **between two known values**, usually in a smooth or linear way.

fractionTowardEnd 应该在 0 ~ 1 之间 

```cpp
float Interpolate( float start, float end, float fractionTowardEnd )
{
	return ( 1 - fractionTowardEnd ) * start + fractionTowardEnd * end;
}
```


```
start = 10
end = 20
fractionTowardEnd = 0.25 → means 25% of the way to the end
```


**Start contribution**: remaining 75% → 10 × 0.75 = 7
**End contribution**: 25% toward end → 20 × 0.25 = 5