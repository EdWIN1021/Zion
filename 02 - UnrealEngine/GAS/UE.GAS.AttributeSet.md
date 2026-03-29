### ATTRIBUTE_ACCESSORS

```cpp
#define ATTRIBUTE_ACCESSORS(ClassName, PropertyName) \  
		GAMEPLAYATTRIBUTE_PROPERTY_GETTER(ClassName, PropertyName) \  
    GAMEPLAYATTRIBUTE_VALUE_GETTER(PropertyName) \  
    GAMEPLAYATTRIBUTE_VALUE_SETTER(PropertyName) \  
    GAMEPLAYATTRIBUTE_VALUE_INITTER(PropertyName)
```


### PostGameplayEffectExecute

This line overrides the `PostGameplayEffectExecute` function to define custom logic that runs **after a Gameplay Effect modifies an attribute** in the AttributeSet.

```cpp
virtual void PostGameplayEffectExecute(const struct FGameplayEffectModCallbackData& Data) override;
```