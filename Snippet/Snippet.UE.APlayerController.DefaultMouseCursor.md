# DefaultMouseCursor

Access Specifier: public
Tags: property
Description: Type of mouse cursor to show by default

## **Declaration**

```cpp
UPROPERTY(EditAnywhere, BlueprintReadOnly, Category=MouseInterface)
TEnumAsByte<EMouseCursor::Type> DefaultMouseCursor;
```

## **Example**

```cpp
DefaultMouseCursor = EMouseCursor::Default;
```