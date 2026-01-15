# Get

Access Specifier: public
Description: Gets a key value pair combination that defines a session setting
Type: Funciton

```cpp
	template<typename ValueType>
	bool Get(FName Key, ValueType& Value) const;
```

```cpp
FString MatchType;
Result.Session.SessionSettings.Get(FName("MatchType"),MatchType);
```