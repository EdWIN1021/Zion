## Create a Weapon Socket on the Skeletal Mesh
![[Screenshot 2025-02-02 164904.png | center]]
## Get Socket By Name

```cpp
const USkeletalMeshSocket* HandSocket = Character->GetMesh()->GetSocketByName(FName("RightHandSocket"));
```

## Attach the Weapon to the Character

![[Screenshot 2025-04-12 054828.png]]

```cpp
HandSocket->AttachActor(EquippedWeapon, Character->GetMesh()); 
FAttachmentTransformRules TransformRules(EAttachmentRule::SnapToTarget, true); 
ItemMesh->AttachToComponent(SlashCharacter->GetMesh(), TransformRules, FName("RightHandSocket"));
```