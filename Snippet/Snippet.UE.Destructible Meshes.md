# Destructible Meshes

## 1. Enter Fracture Mode

- Open the **Modes** dropdown in the Toolbar and select **Fracture**; the Chaos Fracture Editor will appear.
- Drag your Static Mesh into the viewport (or select an existing mesh) to prepare it for conversion into a Geometry Collection

## 2. Create a Geometry Collection

- With the mesh selected, click **New** in the **Fracture** tab of the Mode Toolbar to create a Geometry Collection asset.
- Specify a name and folder in the Content Browser dialog, then hit **Create**; the mesh will now display fracture preview outlines

## 3. Apply a Uniform Fracture

- In the **Fracture** panel, choose **Uniform Voronoi** as the fracture method to generate evenly distributed fracture cells across the mesh.
- Adjust the **Minimum** and **Maximum Sites** sliders to control fragment count, then click **Fracture** to split the Geometry Collection.
- Use **Explode View** (Shift + E / Shift + Q) or press **Shift + B** to toggle the colored bone display and inspect individual fracture levels

## 4. Add and Configure a Field System Actor / Add FieldSystem to a Weapon

- Open the **Place Actors** panel, search for **Field System Actor**, and drag it into your level; this actor includes a Field System Component for Chaos.
- In the Field System Actor’s **Details** panel, assign your **Field System** asset and set up field commands (e.g., **ClusterStrain**, **RadialForce**) to trigger breaks or forces at runtime.

## 5. Configure Your Geometry Collection Asset

1. **Open the Geometry Collection asset** in the Content Browser. Inside its **Collision Settings** section, you can define per‑size collision shapes.
2. Under **Size Specific Data**, find **Collision Shape → Implicit Type** and select **Capsule** (value 3) for the desired data index. This gives each fractured piece a simple analytic capsule collider.
3. Tweak **Collision Object Reduction Percentage** and other thresholds to balance performance and simulation accuracy.

## 6. Enable Overlap Events on the Component

1. **Simulate Physics Requirement**
    
    Geometry Collection Components only generate overlap events if they participate in the physics system. Ensure **Simulate Physics** is checked on your **GeometryCollectionComponent** instance in the Details panel
    
2. **Generate Overlap Events**
    
    In the same Details panel under **Collision**, enable **Generate Overlap Events.** Both this component and any overlapping component must have overlap generation turned on
    
3. **Collision Preset**
    
    Optionally, set **Collision Preset** to something like **OverlapAllDynamic** or a custom profile that overlaps with your player or pawn channels.
    

## 7. Create a C++ Actor with a Geometry Collection Component

- Derive your actor from **AActor** and include the **GeometryCollectionComponent** header

```cpp
 UPROPERTY(VisibleAnywhere)
 UGeometryCollectionComponent* GeometryCollection;
```

## 8. Component Setup in Constructor

```cpp
GeometryCollection->SetGenerateOverlapEvents(true);
```

## 9. Create and Configure a Blueprint Derived from Your Actor