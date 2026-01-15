# Camera and Spring Arm

- SpringArm
    - Camera

### Declare Components in Header

```cpp
USpringArmComponent* CameraBoom;
UCameraComponent* ViewCamera;
```

### Initialize in Constructor

```cpp
CameraBoom= CreateDefaultSubobject<USpringArmComponent>(TEXT("CameraBoom"));
CameraBoom->SetupAttachment(GetRootComponent());
CameraBoom->TargetArmLength = 300.f;

ViewCamera = CreateDefaultSubobject<UCameraComponent>(TEXT("ViewCamera"))
ViewCamera->SetupAttachment(SpringArm);
```