```cpp
Wasp* Game::SpawnNewRandomWasp()
{
	for ( int waspIndex = 0; waspIndex < MAX_WASPS; ++ waspIndex )
	{
		Wasp *& wasp = m_wasps[waspIndex];
		if ( !wasp )
		{
			wasp = new Wasp( this, Rgba8(255, 255, 0), WASP_HEALTH );
			wasp->m_position = GetRandomOffscreenPositionForObject( wasp->m_cosmeticRadius );
			return wasp;
		}
	}
	return nullptr;
}
```
