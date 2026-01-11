## Introduction

An **Overlap Event** occurs when two actors intersect or overlap within the game world. These events are useful for detecting collisions between objects, characters, or other interactive elements.

---

## Adding a Collision Component

To enable collision detection and generate Overlap Events, you need to add a collision component to your actor. Here's how to create a Sphere Component:

```cpp
Sphere = CreateDefaultSubobject<USphereComponent>(TEXT("Sphere"));
```

This creates a spherical collision volume that will trigger overlap events when other actors enter or exit the sphere.

---

## Implementing Overlap Functions

You can handle overlap events by implementing the following functions in your actor class:

### Begin Overlap Event

```cpp
UFUNCTION()
void OnSphereBeginOverlap(UPrimitiveComponent* OverlappedComponent, AActor* OtherActor, UPrimitiveComponent* OtherComp, int32 OtherBodyIndex, bool bFromSweep, const FHitResult& SweepResult);
```

- **Purpose**: Called when an actor enters the collision volume.
- **Parameters**:
    - `OverlappedComponent`: The component that detected the overlap.
    - `OtherActor`: The actor that entered the collision volume.
    - `OtherComp`: The component of the other actor involved in the overlap.
    - `OtherBodyIndex`: Index of the body part (for characters with multiple bodies).
    - `bFromSweep`: Whether the overlap was caused by a sweeping motion.
    - `SweepResult`: Contains detailed hit information.

### End Overlap Event

```cpp
UFUNCTION()
void OnSphereEndOverlap(UPrimitiveComponent* OverlappedComponent, AActor* OtherActor, UPrimitiveComponent* OtherComp, int32 OtherBodyIndex);
```

- **Purpose**: Called when an actor exits the collision volume.
- **Parameters**:
    - `OverlappedComponent`: The component that detected the overlap.
    - `OtherActor`: The actor that exited the collision volume.
    - `OtherComp`: The component of the other actor involved in the overlap.
    - `OtherBodyIndex`: Index of the body part (for characters with multiple bodies).

---

## Binding Callback Functions
To ensure your overlap functions are called, bind them to the collision component:
```cpp
void AItem::BeginPlay()
{
    Super::BeginPlay();

    // Bind Begin Overlap event
    Sphere->OnComponentBeginOverlap.AddDynamic(this, &AItem::OnSphereBeginOverlap);

    // Bind End Overlap event
    Sphere->OnComponentEndOverlap.AddDynamic(this, &AItem::OnSphereEndOverlap);
}
```

- **Explanation**: The `AddDynamic` method links the component's overlap events to your custom functions. This ensures that `OnSphereBeginOverlap` and `OnSphereEndOverlap` are called whenever an actor enters or exits the sphere.
