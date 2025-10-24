![[IMG_0021.png | center | 600]]

![[IMG_0022.png | center | 700]]


```cpp
float GetShortestAngularDispDegrees( float startDegrees, float endDegrees )
{
	float displacement = endDegrees - startDegrees;

	while ( displacement > 180 )  { 
		displacement -= 360;
	}

	while ( displacement < -180 ) {
		displacement += 360;
	}

	return displacement;
}
```