---
tags:
  - AI
---
Pathfinding is essential for efficient navigation in game development and refers to the processing of determining the optimal path while simulating the movement from one point to another.

A Navigation mesh, which is a data structure that represents the walkable surface of a level.


### 1. Show Navigation

- **Command:** `show navigation`
- **Explanation:** This command displays the navigation mesh in the viewport, allowing you to visualize and debug the navigation system.

---

### 2. Edit Project Settings

#### a. Runtime Generation

- Navigate to:
    
    ```
  Edit → Project Settings → Navigation Mesh → Runtime
    ```
    
- Set **Runtime Generation** to: `Dynamic`
- **Explanation:** Dynamic generation allows the navigation mesh to be generated at runtime based on the environment, making it more flexible and suitable for dynamic levels or environments.

#### b. Nav Mesh Resolution Parameters

- Navigate to:
    
    ```
  Edit → Project Settings → Navigation Mesh → Generation → Nav Mesh Resolution Params → Default
    ```
    
- Adjust the following parameters:
    - **CellSize**
        - **Explanation:** This is the size of each cell in the navigation mesh. A smaller value increases precision but may reduce performance, while a larger value improves performance at the cost of some precision.
				
    - **CellHeight**
        - **Explanation:** This determines the vertical resolution of the navigation mesh, affecting how accurately the system handles height changes (e.g., stairs or slopes).

---

### 3. Add Nav Mesh Bounds Volume

- Quick action:
    
    ```
    Quickly Add to the project → Volumes → Nav Mesh Bounds Volume
    ```
    
- **Explanation:** The Nav Mesh Bounds Volume defines the area in which the navigation mesh will be generated. It ensures that the mesh is only created within relevant areas of the level, improving performance.

---

### 4. P Key to Show the Nav Mesh

- **Command:** Press `P` to show the navigation mesh.
- **Explanation:** This allows you to visualize the navigation mesh in the viewport, helping you debug and ensure that the mesh is correctly generated and covers the intended areas.

---

### 5. Actor Setup for AI

#### a. Possessing AI

- Ensure AI actors are:
    - Placed in World or Spawned
- **Explanation:** AI actors need to be properly placed in the world or spawned dynamically to function within the navigation system.

#### b. Movement Functionality

- Use the `MoveToActor` function for AI movement.
- Reference: [MoveToActor](https://www.notion.so/MoveToActor-1dc8d590ff3880798bacc4b00cb1468f?pvs=21)
- **Explanation:** The `MoveToActor` function enables AI actors to move towards a target, such as another actor or a specific point in the world.

#### c. Target Point

- Define a target point for AI movement.
- **Explanation:** The target point is where the AI actor will navigate to using the navigation mesh. This could be another actor, a static location, or a dynamic point determined at runtime.

