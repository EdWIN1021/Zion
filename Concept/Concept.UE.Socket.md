## Create Socket on Skeletal Mesh
![[Screenshot 2025-02-02 164904.png | center | 550]]

## Create Socket on Static Mesh

![[Screenshot 2025-12-19 191509.png | center]]


## Get Socket By Name
```cpp
const USkeletalMeshSocket* HandSocket = Character->GetMesh()->GetSocketByName(FName("RightHandSocket"));
```

## Attach the Weapon to the Character

![[Screenshot 2025-04-12 054828.png | center]]

```cpp
HandSocket->AttachActor(EquippedWeapon, Character->GetMesh()); 
FAttachmentTransformRules TransformRules(EAttachmentRule::SnapToTarget, true); 
ItemMesh->AttachToComponent(SlashCharacter->GetMesh(), TransformRules, FName("RightHandSocket"));
```