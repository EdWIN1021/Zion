# GetSessionInterface

Description: The session interface allows you to create, manage, find, and join online sessions.

- Declares a thread-safe shared pointer to an object of type `IOnlineSession`

```cpp
TSharedPtr<class IOnlineSession, ESPMode::ThreadSafe> OnlineSessionInterface;
```

- Retrieving the session interface from the online subsystem

```cpp
OnlineSessionInterface = OnlineSubsystem->GetSessionInterface();
```