# Damage System

## 1. Setting Owner and Instigator on the Damage Causer

```cpp
	SetOwner(NewOwner);
	SetInstigator(NewInstigator);
```

## Applying Damage with [`ApplyDamage`](https://www.notion.so/ApplyDamage-1da8d590ff3880ea9512e8516a7e0ee7?pvs=21)

```cpp
		UGameplayStatics::ApplyDamage(
			BoxHit.GetActor(),
			Damage,
			GetInstigator()->GetController(),
			this,
			UDamageType::StaticClass()
		);
```

## 2. Overriding [`TakeDamage`](https://www.notion.so/TakeDamage-1da8d590ff38805d9049d628321de977?pvs=21) on the Victim

```cpp
float AEnemy::TakeDamage(float DamageAmount, struct FDamageEvent const& DamageEvent, class AController* EventInstigator, AActor* DamageCauser)
{
	if (Attributes && HealthBarWidget)
	{
		Attributes->ReceiveDamage(DamageAmount);
		HealthBarWidget -> SetHealthPercent(Attributes->GetHealthPercent());
	}
	return DamageAmount;
}
```