```cpp
HandSocket->AttachActor( EquippedWeapon, Character->GetMesh() ); 

FAttachmentTransformRules TransformRules( EAttachmentRule::SnapToTarget, true ); 
ItemMesh->AttachToComponent( SlashCharacter->GetMesh(), TransformRules, FName( "RightHandSocket" ) );
```