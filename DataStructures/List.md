```cpp
StatModifier modToAdd = new StatModifier(value, source);
```

### Add
```cpp
modifiers.Add(modToAdd);
```

### RemoveAll
```CPP
modifiers.RemoveAll(modifier => modifier.source == source);
```