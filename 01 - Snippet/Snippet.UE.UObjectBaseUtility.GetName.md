# GetName

Access Specifier: public

## **Declaration**

```cpp
FORCEINLINE FString GetName() const
{
	return GetFName().ToString();
}
```

## **Example**

```cpp
checkf(WeaponOwningPawn, TEXT("Forgot to assign an instigator as the owning pawn for the weapon %s"), *GetName());
```