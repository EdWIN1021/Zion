# Project Class

### Create a [AActor](https://www.notion.so/AActor-1378d590ff38800d88b2cf3de65abc6a?pvs=21) Class

```cpp
	UPROPERTY(VisibleDefaultsOnly, BlueprintReadOnly, Category = "Projectile")
	UBoxComponent* ProjectileCollisionBox;

	UPROPERTY(VisibleDefaultsOnly, BlueprintReadOnly, Category = "Projectile")
	UNiagaraComponent* ProjectileNiagaraComponent;

	UPROPERTY(VisibleDefaultsOnly, BlueprintReadOnly, Category = "Projectile")
	UProjectileMovementComponent* ProjectileMovementComponent;
```

### Create a collision box component and set it as the root component

```cpp
	ProjectileCollisionBox = CreateDefaultSubobject<UBoxComponent>(TEXT("ProjectileCollisionBox"));
	SetRootComponent(ProjectileCollisionBox);
	
	ProjectileCollisionBox->SetCollisionEnabled(ECollisionEnabled::QueryOnly);
	ProjectileCollisionBox->SetCollisionResponseToChannel(ECC_Pawn, ECR_Block);
	ProjectileCollisionBox->SetCollisionResponseToChannel(ECC_WorldDynamic, ECR_Block);
	ProjectileCollisionBox->SetCollisionResponseToChannel(ECC_WorldStatic, ECR_Block);
```

### Create Niagara particle system component and attach it to the root

```cpp
	ProjectileNiagaraComponent = CreateDefaultSubobject<UNiagaraComponent>(TEXT("ProjectileNiagaraComponent"));
	ProjectileNiagaraComponent->SetupAttachment(GetRootComponent());
```

### Create projectile movement component and configure speed

```cpp
ProjectileMovementComponent = CreateDefaultSubobject<UProjectileMovementComponent>(TEXT("ProjectileMovementComponent"));
ProjectileMovementComponent->InitialSpeed = 700.f; // Speed when fired
ProjectileMovementComponent->MaxSpeed = 900.f;     // Max speed cap

// Directly set velocity to move in +X direction
// ⚠️ This overrides InitialSpeed and MaxSpeed behavior
ProjectileMovementComponent->Velocity = FVector(1.f, 0.f, 0.f);

// Disable gravity for this projectile (no arc, straight-line motion)
ProjectileMovementComponent->ProjectileGravityScale = 0.f;
```

### Automatically destroy the projectile after 4 seconds

```cpp
InitialLifeSpan = 4.f;
```