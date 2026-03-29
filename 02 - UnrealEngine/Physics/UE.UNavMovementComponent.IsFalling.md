Returns true if currently falling (not flying, in a non-fluid volume, and not on the ground)

```cpp
	UFUNCTION(BlueprintCallable, Category="AI|Components|NavMovement")
	ENGINE_API virtual bool IsFalling() const;
```