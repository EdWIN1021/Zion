$$
\vec{A} \cdot \vec{B} = \| \vec{A} \| \, \| \vec{B} \| \cos(\theta)
$$
$\|\vec{A}\|$ is the magnitude of $\vec{A}$
$\|\vec{B}\|$ is the magnitude of $\vec{B}$
$\theta$ is the angle between $\vec{A}$ and $\vec{B}$

The dot product of $\vec{V}$ with unit vector $\widehat{N}$, denoted $\vec{V} \cdot \widehat{N}$, is defined to be the projection of $\vec{V}$ in the direction of $\hat{N}$

Positive if the two vectors are pointing in similar directions
Negative if the two vectors are pointing in nearly opposite directions

when $\theta =  0$, the two vectors point in exactly the same direction.
when $\theta =  \frac{\pi}{2}$, the two vectors are precisely perpendicular to each other. (no shadow) 


```cpp
float DotProduct2D( Vec2 const& a, Vec2 const& b )
{
	return a.x * b.x + a.y * b.y;;
}
```
