# Field System Actors

## 1. Add a Radial Falloff Field

- **Open your Field System asset**
    - In the Content Browser, locate and double‑click your **Field System** (or open the Field System graph inside your Blueprint).
- **Insert the Radial Falloff node**
    - Right‑click in the graph, search for **Set Radial Falloff**, and select **Field → Set Radial Falloff**.
- **Configure falloff parameters**
    - **Center Position**: Set to your desired epicenter (e.g. the actor location or a socket transform).
    - **Sphere Radius**: Defines how far the field extends.
    - **Field Magnitude**: Maximum strength at the center.
    - **Min/Max Range**: Controls the mapping of normalized distance to magnitude.
    - **Default Value**: Value applied outside the radius (often 0 to disable beyond range).

## 2. Add a MetaData Filter for Destruction

- **Insert the MetaData Filter node**
    - Right‑click in the same graph, search for **Set Meta Data Filter**, and pick **Field → Set Meta Data Filter**.
- **Configure the Object Type**
    - In the filter’s **Details** panel, set **Object Type** to **Destruction**.
    - (Leave **State Type** and **Position Type** as defaults unless you need additional constraints.)

![屏幕截图 2025-04-17 022305.png](Field%20System%20Actors/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_2025-04-17_022305.png)