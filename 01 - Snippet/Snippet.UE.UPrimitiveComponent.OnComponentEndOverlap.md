# OnComponentEndOverlap

Access Specifier: public
Type: Properites

## **Declaration**

```cpp
UPROPERTY(BlueprintAssignable, Category="Collision")
FComponentEndOverlapSignature OnComponentEndOverlap;

```

## **Example**

```cpp
WeaponCollisionBox->OnComponentEndOverlap.AddUniqueDynamic(this, &ThisClass::OnCollisionBoxEndOverlap);

UFUNCTION()
virtual void OnCollisionBoxEndOverlap(UPrimitiveComponent* OverlappedComponent, AActor* OtherActor, UPrimitiveComponent* OtherComp, int32 OtherBodyIndex);
```