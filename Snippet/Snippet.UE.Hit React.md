This document outlines the implementation details of the hit reaction system in C++.

## Overview

The system calculates the angle between the actor's forward direction and the impact point to determine which animation montage to play. The process involves:

1. Projecting the impact point onto the horizontal plane
2. Calculating vectors and angles
3. Determining left/right using cross product
4. Classifying into sections for animation playback

---

## 1. Projecting onto Horizontal Plane

```cpp
const FVector ImpactLowered(ImpactPoint.X, ImpactPoint.Y, GetActorLocation().Z);
```

- **Purpose**: Drops the Z component to ignore vertical differences in calculations.
- **Explanation**: Creates a new vector with X and Y from `ImpactPoint` and Z from actor's current location.

---

## 2. Computing Direction Vector

```cpp
const FVector ToHit = (ImpactLowered - GetActorLocation()).GetSafeNormal();
```

- **Purpose**: Calculate unit vector pointing towards impact location.
- **Explanation**:
    - Subtracts actor's location from projected impact point.
    - `GetSafeNormal()` ensures the result is a unit vector.

---

## 3. Calculating Angle with Dot Product

```cpp
const double CosTheta = FVector::DotProduct(Forward, ToHit);
```

- **Purpose**: Find cosine of angle between forward direction and hit location.
- **Explanation**:
    - `FVector::DotProduct()` returns the dot product of two vectors.
    - This value is equal to the cosine of the angle between them.

---

## 4. Converting Cosine to Degrees

```cpp
double Theta = FMath::Acos(CosTheta);
Theta = FMath::RadiansToDegrees(Theta);
```

- **Purpose**: Convert angle from radians to degrees.
- **Explanation**:
    - `FMath::Acos()` returns the angle in radians.
    - Converted to degrees for easier interpretation.

---

## 5. Determining Left vs. Right with Cross Product

```cpp
const FVector CrossProduct = FVector::CrossProduct(Forward, ToHit);
if (CrossProduct.Z < 0)
{
    Theta *= -1.f;
}
```

- **Purpose**: Determine if impact is to left or right of forward direction.
- **Explanation**:
    - `FVector::CrossProduct()` returns a vector perpendicular to both inputs.
    - The Z component indicates direction:
        - Negative → Right
        - Positive → Left

---

## 6. Classifying into Quadrants

```cpp
FName Section("FromBack");

if (Theta >= -45.f && Theta < 45.f)
    Section = "FromFront";
else if (Theta >= -135.f && Theta < -45.f)
    Section = "FromLeft";
else if (Theta >= 45.f && Theta < 135.f)
    Section = "FromRight";
```

- **Purpose**: Classify the impact direction into one of four sections.
- **Explanation**:
    - Angles are mapped as follows:
        - (-45°, 45°): Front
        - (45°, 135°): Right
        - (-135°, -45°): Left
        - All other cases: Back

---

## 7. Playing the Montage

```cpp
PlayHitReactMontage(Section);
```

- **Purpose**: Trigger animation based on impact direction.
- **Explanation**:
    - `PlayHitReactMontage()` takes the section name and plays the corresponding animation.