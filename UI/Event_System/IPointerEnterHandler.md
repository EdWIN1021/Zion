The `IPointerEnterHandler` interface in Unity is used to detect when a mouse cursor or touch enters the area of a UI element.

```cpp
using UnityEngine;
using UnityEngine.EventSystems; // Must import this namespace

public class HoverEffect : MonoBehaviour, IPointerEnterHandler  // Implement the interface
{
    // This method is called when the pointer enters this object
    public void OnPointerEnter(PointerEventData eventData)
    {
        Debug.Log("Mouse entered!");
    }
}
```


