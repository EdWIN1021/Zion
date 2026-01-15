# Set

Description: This setting can be used to store additional information about the session, such as the type of match, and advertise it to other players so they can filter or join sessions based on this information.
Type: Funciton

```cpp
/**
* @param Key key for the setting
* @param Value value of the setting
* @param InType type of online advertisement
*/

template<typename ValueType>
void Set(FName Key, const ValueType& Value, EOnlineDataAdvertisementType::Type InType);
```

```cpp
	// ViaPing: The setting is included in ping responses, making it available for LAN matches.
	SessionSettings->Set(FName("MatchType"), FString("FreeForAll"), EOnlineDataAdvertisementType::ViaOnlineServiceAndPing);
```