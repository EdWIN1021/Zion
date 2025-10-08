
> [!NOTE] Title
> Gradually rotates `currentDegrees` toward `goalDegrees`, but **limits each step to at most maxDeltaDegrees **.
### maxDeltaDegrees
The maximum angle (in degrees) that can be turned toward the target in a single step.


---

```cpp
float GetTurnedTowardDegrees( float currentDegrees, float goalDegrees, float maxDeltaDegrees )
{
	float angularDisplacement = GetShortestAngularDispDegrees( currentDegrees, goalDegrees );

	if ( angularDisplacement > -maxDeltaDegrees && angularDisplacement < maxDeltaDegrees )
	{
		return goalDegrees;
	}

	return angularDisplacement > 0.0f ? ( currentDegrees + maxDeltaDegrees ) : ( currentDegrees - maxDeltaDegrees );
}
```
