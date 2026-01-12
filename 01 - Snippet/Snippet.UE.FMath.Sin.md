# Sin

```cpp
void AItem::Tick(float DeltaTime)
{
	Super::Tick(DeltaTime);

	RunningTIme += DeltaTime;
	float DeltaZ = 0.25f * FMath::Sin(RunningTIme * 5.f);
	AddActorWorldOffset(FVector(0.f, 0.f, DeltaZ));
}
```