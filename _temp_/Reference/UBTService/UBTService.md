---
Category: Class
---
```cpp
UCLASS()  
class WARRIOR_API UBTService_OrientToTargetActor : public UBTService  
{  
    GENERATED_BODY()  
    UBTService_OrientToTargetActor();  
  
    virtual void InitializeFromAsset(UBehaviorTree& Asset) override;  
    virtual FString GetStaticDescription() const override;  
    virtual void TickNode(UBehaviorTreeComponent& OwnerComp, uint8* NodeMemory, float DeltaSeconds) override;  
  
    UPROPERTY(EditAnywhere, Category = "Target")  
    FBlackboardKeySelector InTargetActorKey;  
  
    UPROPERTY(EditAnywhere, Category = "Target")  
    float RotationInterpSpeed;  
      
};
```

```cpp
UBTService_OrientToTargetActor::UBTService_OrientToTargetActor()  
{  
    NodeName = TEXT("Native Orient Rotation To Target Actor");  
  
    INIT_SERVICE_NODE_NOTIFY_FLAGS();  
      
    RotationInterpSpeed = 5.f;  
    Interval = 0.f;  
    RandomDeviation = 0.f;  
  
    InTargetActorKey.AddObjectFilter(this, GET_MEMBER_NAME_CHECKED(ThisClass, InTargetActorKey), AActor::StaticClass());  
}  
  
void UBTService_OrientToTargetActor::InitializeFromAsset(UBehaviorTree& Asset)  
{  
    Super::InitializeFromAsset(Asset);  
  
    if (UBlackboardData* BBAsset =  GetBlackboardAsset())  
    {  
       InTargetActorKey.ResolveSelectedKey(*BBAsset);  
    }  
}  
  
FString UBTService_OrientToTargetActor::GetStaticDescription() const  
{  
    const FString KeyDescription = InTargetActorKey.SelectedKeyName.ToString();  
    return FString::Printf(TEXT("Orient rotation to %s Key %s"), *KeyDescription, *GetStaticServiceDescription());  
}  
  
void UBTService_OrientToTargetActor::TickNode(UBehaviorTreeComponent& OwnerComp, uint8* NodeMemory, float DeltaSeconds)  
{  
    Super::TickNode(OwnerComp, NodeMemory, DeltaSeconds);  
  
    UObject* ActorObject  = OwnerComp.GetBlackboardComponent()->GetValueAsObject(InTargetActorKey.SelectedKeyName);  
    AActor* TargetActor = Cast<AActor>(ActorObject);  
  
    APawn* OwningPawn = OwnerComp.GetAIOwner()->GetPawn();  
  
    if (OwningPawn && TargetActor)  
    {  
       const FRotator LookAtRot = UKismetMathLibrary::FindLookAtRotation(OwningPawn->GetActorLocation(), TargetActor->GetActorLocation());  
       const FRotator TargetRot = FMath::RInterpTo(OwningPawn->GetActorRotation(), LookAtRot, DeltaSeconds, RotationInterpSpeed);  
         
       OwningPawn->SetActorRotation(TargetRot);  
    }  
}
```

