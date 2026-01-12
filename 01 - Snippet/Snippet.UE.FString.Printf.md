# Printf

<aside>

- using `*Name` converts the `FString` into a C-style string (`const TCHAR*`), which is required by functions that use the `%s` format specifier (for example, in `UE_LOG` or `FString::Printf`).
</aside>

```cpp
FString Name = GetName();
FString::Printf(TEXT("Item Name: %s", *Name);
```

```cpp
FString::Printf(TEXT("<Default>%s, </><Level>%d</>"), L"Default Ability Name - LoremIpsum", Level);
```