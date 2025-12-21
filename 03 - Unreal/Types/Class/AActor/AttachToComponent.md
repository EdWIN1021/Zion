---
Class: "[[AActor]]"
Category: Function
Description:
Return Type:
---
## **Declaration**

```cpp
ENGINE_API virtual bool AttachToComponent(USceneComponent* InParent, const FAttachmentTransformRules& AttachmentRules, FName InSocketName = NAME_None );
```

## **Example**

```cpp
FAttachmentTransformRules TransformRules( EAttachmentRule::SnapToTarget, true ); 
ItemMesh->AttachToComponent( SlashCharacter->GetMesh(), TransformRules, FName("RightHandSocket") );
```
