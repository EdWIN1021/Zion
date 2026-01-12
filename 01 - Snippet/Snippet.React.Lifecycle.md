# Lifecycle

Owner: Edwin

![Screenshot 2023-11-09 at 2.59.32 PM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2023-11-09_at_2.59.32_PM.png)

---

## Render is Triggered

![Screenshot 2024-02-04 at 8.48.03 AM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2024-02-04_at_8.48.03_AM.png)

- Initial render of the application
- State is update in one or more component instances (re-render)

## Render Phase

![Screenshot 2023-11-09 at 2.54.12 PM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2023-11-09_at_2.54.12_PM.png)

### Virtual DOM

- virtual Dom is a tree of all react elements created from all instances in the component tree.

### Fiber

- The Fiber tree is a tree-like structure that mirrors the structure of the React component tree (Virtual Dom).
- Each node in the Fiber tree, called a "fiber," represents a React element or component.
- NOT re-created on every render

### Reconciliation

- Deciding which DOM elements actually need to be inserted, deleted or updated, in order to reflect the latest state changes.
- Can be paused, reused, or thrown away.

### Diffing

- **Same** position, **Different** element
    
    ![Screenshot 2023-11-09 at 3.33.15 PM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2023-11-09_at_3.33.15_PM.png)
    
    - entire sub-tree is no longer valid.
    - old components are destroyed and removed from DOM. ( including state )
    - Tree might be rebuild is children stayed the same. (state is reset)
    
- **Same** position, **Same** element
    
    ![Screenshot 2023-11-09 at 3.38.01 PM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2023-11-09_at_3.38.01_PM.png)
    
    - Element will be kept (as well as child elements), including state.
    - New props / attributes are passed if they changed between renders.
    
- Key prop
    - tell the diffing algorithm that an element is unique.
    - to distinguish between multiple instances of the same component type.
    - react will re-create entire list if there is no key prop

## Commit phase

![Screenshot 2023-11-09 at 3.40.40 PM.png](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/Screenshot_2023-11-09_at_3.40.40_PM.png)

- react writes to the DOM: insertions, deletions, and updates.
- committing is synchronous: DOM is updated in one go, it can’t be interrupted.
- workInProgress fiber tree becomes the current tree for the next render cycle.

[methods](Lifecycle%20d8d943b6195b4c779b1472719ecb2acd/methods%20a429974c748f4e689ae1f07775a5edc2.md)