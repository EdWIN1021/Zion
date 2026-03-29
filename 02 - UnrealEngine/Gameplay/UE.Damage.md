This document outlines the key components and implementation details for a damage system in your game.

## 1. Setting Owner and Instigator on the Damage Causer

The owner and instigator are crucial for tracking who caused the damage and who is responsible for the damage logic.

```cpp
	SetOwner(NewOwner);
	SetInstigator(NewInstigator);
```

- **`SetOwner()`**: Sets the owner of the damage component, typically used to track the entity that "owns" the damage logic.
- **`SetInstigator()`**: Sets the instigator of the damage event, which is the actor or controller causing the damage.

These functions are essential for debugging and gameplay logic, as they help trace back who or what caused a specific damage event.

---

## 2. Applying Damage with `ApplyDamage`

The `ApplyDamage` function is used to deal damage to an actor.

```cpp
	UGameplayStatics::ApplyDamage(
		BoxHit.GetActor(),
		Damage,
		GetInstigator()->GetController(),
		this,
		UDamageType::StaticClass()
	);
```

### Parameters:

- **`BoxHit.GetActor()`**: The target actor being damaged (e.g., an enemy or player).
- **`Damage`**: The amount of damage to apply.
- **`GetInstigator()->GetController()`**: The controller causing the damage (used for tracking and AI purposes).
- **`this`**: A reference to the damage source (e.g., a weapon or projectile).
- **`UDamageType::StaticClass()`**: The type of damage being applied (e.g., melee, ranged, fire).

### Notes:

- This function is typically called from a weapon or projectile component.
- Make sure the target actor has the necessary attributes to receive damage.

---

## 3. Overriding `TakeDamage` on the Victim

The `TakeDamage` function is called when an actor receives damage.

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

### Explanation:

- **`TakeDamage()`**: This function is called when an actor takes damage. It updates the actor's health and notifies any relevant systems (e.g., UI, AI).
- **`Attributes`**: A reference to the actor's attributes (health, stamina, etc.).
- **`HealthBarWidget`**: The widget used to display health visually.

### Notes:

- Always ensure that `Attributes` and `HealthBarWidget` are valid before accessing them.
- You can override this function in different classes (e.g., `AEnemy`, `APawn`) to customize damage handling.

---

## Summary

The damage system consists of three main components:

1. **Setting owner and instigator**: Track who caused the damage.
2. **Applying damage**: Deal damage to a target using `ApplyDamage`.
3. **Handling damage reception**: Implement `TakeDamage` to update attributes and UI.

