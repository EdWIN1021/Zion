
```C++
void TransformVertexArrayXY3D( int numVerts, Vertex* verts, float uniformScaleXY, float rotationDegreesAboutZ, Vec2 const& translationXY )
{
	for( int vertIndex = 0; vertIndex < numVerts; ++ vertIndex )
	{
		Vec3& pos = verts[ vertIndex ].m_position;
		TransformPositionXY3D( pos, uniformScaleXY, rotationDegreesAboutZ, translationXY );
	}
}
```