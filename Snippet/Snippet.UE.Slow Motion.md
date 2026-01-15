# Slow Motion

### **1. Create Animation Notify State Blueprint**

1. Right-click in Content Browser
2. Select **`Blueprint Class`**
3. Search for **`AnimNotifyState`** and create it
4. Name it **`NS_GlobalTimeDilation`**

### **2. Override Notify Functions**

**Open the Blueprint and add:**

```
Event Received Notify Begin
Event Received Notify End
```

### **3. Add Configurable Variable (Best Practice)**

1. Add a float variable **`TimeDilationValue`**
2. Set default value to 0.2 (for slow-mo effect)
3. Make variable **`Editable`** and **`Expose on Spawn`**

### **4. Blueprint Setup**

**Received_NotifyBegin:**

- Drag from **`Return Value`** pin and cast to your character class
- Add **`Set Global Time Dilation`** node with **`TimeDilationValue`**

**Received_NotifyEnd:**

- Same cast structure
- Set Time Dilation back to 1.0

### **5. Add to Animation Montage**

1. Open your AnimMontage
2. In the timeline:
    - Right-click where you want the effect to start
    - Add your **`NS_GlobalTimeDilation`**
3. Set properties:
    - Duration: How long the effect should last
    - TimeDilationValue: Your desired slow-mo factor (0-1)