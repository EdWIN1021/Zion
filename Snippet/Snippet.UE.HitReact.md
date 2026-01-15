# HitReact

**1. Projecting onto the Horizontal Plane**

```cpp
const FVector ImpactLowered(ImpactPoint.X, ImpactPoint.Y, GetActorLocation().Z);
```

- Drops the Z component of the impact so that vertical differences don’t affect the horizontal direction calculation.

**2. Computing the Direction Vector**

```cpp
const FVector ToHit = (ImpactLowered - GetActorLocation()).GetSafeNormal();
```

- Subtracts the actor’s location from the projected impact point and normalizes to get a unit vector pointing toward the hit location.

**3. Calculating the Angle with the Dot Product**

```cpp
const double CosTheta = FVector::DotProduct(Forward, ToHit
```

- The dot product of two unit vectors yields the cosine of the angle between them.

**4. Converting Cosine to Degrees**

```cpp
double Theta = FMath::Acos(CosTheta);
Theta = FMath::RadiansToDegrees(Theta
```

- `FMath::Acos` returns an angle in radians from the cosine.
- Converted to degrees.

**5. Determining Left vs. Right with the Cross Product**

```cpp
const FVector CrossProduct = FVector::CrossProduct(Forward, ToHit);
if (CrossProduct.Z < 0)
{
    Theta *= -1.f;
}
```

- The sign of the Z component of the cross product indicates whether `ToHit` lies to the right (negative Z) or left (positive Z) of `Forward`

**6. Classifying into Quadrants**

```cpp
FName Section("FromBack");

if (Theta >= -45.f && Theta < 45.f)
    Section = "FromFront";
else if (Theta >= -135.f && Theta < -45.f)
    Section = "FromLeft";
else if (Theta >= 45.f && Theta < 135.f)
    Section = "FromRight";
```

- Angles in (‑45°, 45°) → front, (45°, 135°) → right, (‑135°, ‑45°) → left, else → back.

**7. Playing the Montage**

```cpp
PlayHitReactMontage(Section);
```

- Triggers the animation corresponding to the impact direction.