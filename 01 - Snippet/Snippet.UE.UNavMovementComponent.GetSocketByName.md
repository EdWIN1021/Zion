# GetSocketByName

Access Specifier: public
Description: SkeletalMeshSocket of named socket on the skeletal mesh component, or NULL if not found.

```cpp
ENGINE_API class USkeletalMeshSocket const* GetSocketByName( FName InSocketName ) const;
```

```cpp
const USkeletalMeshSocket* HandSocket = Character->GetMesh()->GetSocketByName(FName("RightHandSocket"));
```