# GetDeltaSeconds

Access Specifier: public
Description: Returns the frame delta time in seconds adjusted by e.g. time dilation

## **Declaration**

```cpp
float GetDeltaSeconds() const;
```

## **Example**

```cpp
FollowTime += GetWorld()->GetDeltaSeconds();
```