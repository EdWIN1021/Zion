This document outlines how to create and configure weapon trails in your game using Niagara effects.

## Add the Notify State to Your Animation

To trigger the weapon trail effect during animation, follow these steps:

1. **Open the Animation Sequence or Anim Montage**:
    
    - Navigate to your project's content browser.
    - Double-click on your desired animation asset (e.g., `WeaponAttack.anim`).
2. **Access the Notifies Track**:
    
    - In the animation editor, locate the **Notifies** track below the timeline.
3. **Add a Timed Niagara Effect Notify State**:
    
    - Right-click on the notifies track at the desired frame range.
    - Select **Add Notify State → Timed Niagara Effect** from the context menu.
4. **Configure the Notify State**:
    
    - A colored bar representing the notify state will appear. Click on it to view its properties in the **Details** panel.
    - Adjust the start and end frames as needed to match your animation sequence.


## Assign the Niagara System and Socket

- **Niagara System** asset (e.g., `WeaponTrail_Niagara`).
- Configure the **Socket Name**

