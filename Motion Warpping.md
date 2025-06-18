## Introduction

Motion Warping is a powerful tool in Unreal Engine that allows characters to move more naturally by adjusting their motion paths based on specific rules or targets. This guide will walk you through the setup process using the Motion Warping plugin, enabling you to enhance your character's movement mechanics.

## Step-by-Step Setup

### 1. Enabling the Motion Warping Plugin

To utilize the Motion Warping features, you first need to enable the plugin within Unreal Engine:

1. **Open the Plugins Menu**:
    - Navigate to `Edit -> Plugins` in the top menu bar.
2. **Locate and Enable**:
    - Scroll through the list of plugins until you find "Motion Warping."
    - Check the box next to it to enable the plugin.
		

### 2. Adding the Motion Wrapping Component

Once the plugin is enabled, you can add the Motion Wrapping Component to your character in Blueprints:

1. **Open Your Character Blueprint**:
    - Double-click on your character's blueprint in the Content Browser to open it for editing.
		
2. **Add the Component**:
    - Right-click within the Blueprint graph and select `Add Component`.
    - From the available options, search for or select "Motion Wrapping Component" and add it to your character.

```cpp title:Build.cpp
PublicDependencyModuleNames.AddRange(new string[] { "MotionWarping" });
```

```cpp title:Header
UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category="MotionWarping")  
UMotionWarpingComponent* WarpingComponent;
```

	
### 3. Configuring Animation Montage with Notify States


1. **Open Your Animation Montage**:
    
    - Navigate to the `Content Browser` and open your desired animation montage.
2. **Insert a Notify State**:
    
    - Right-click within the timeline of your montage and select `Add Key`.
    - Choose `Notify State` from the options, name it "Motion Warping," and place it at an appropriate point in the timeline.
3. **Select and Configure the Notify State**:
    
    - Click on the newly added notify state to open its properties.
    - In the details panel, under `Root Motion Modifier`, select `Skew Warp`.
    - Set `Warp Target Name` to your target (e.g., "CombatTarget").
    - Enable `Warp Translation` and set `Ignore ZAxis` to true if you want to ignore vertical movement.
    - Check `Wrap Rotation` and set `Rotation Type` to `Facing` to ensure the character faces the target during warping.
		

### 4. Testing and Fine-Tuning

After setting up, it's crucial to test your configuration:

1. **Create a Test Level**:
    
    - Develop a simple level with your character and a target (another actor or point).
2. **Observe Character Movement**:
    
    - Play the level and monitor how your character moves towards the target.
    - Adjust settings as needed based on observed behavior.
3. **Experiment with Parameters**:
    
    - Modify `Warp Translation` and `Ignore ZAxis` to see their effects on movement.
    - Test different `Rotation Types` to find the most natural facing direction for your character.
		

### 5. Integrating with Existing Animations

Consider how motion warping interacts with your existing animations:

1. **Test Complex Animations**:
    
    - Apply motion warping to characters performing complex actions and observe any interference or enhancement.
2. **Adjust Parameters Dynamically**:
    
    - If necessary, write custom code to update target positions or modify warp parameters during runtime based on game logic.
		

### Conclusion

Motion Warping offers significant potential for enhancing character movement in your games. By following this guide, you can effectively set up and configure the Motion Warping plugin, allowing your characters to move more naturally and responsively. Remember that experimentation and fine-tuning are key to achieving optimal results tailored to your specific game design needs.