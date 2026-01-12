# Client Components

## Concept

- interactive UI ⇒ Client Components
- The “[**use client**](../API%2068f0b11a85ab45c3acfde9fb4ac10a12/use%20client%206d42a8cdf3024228a04657ec20ba8809.md)” directive is a convention to declare a boundary between a Server and Client Component module graph
- importing a Server Component in a Client Component **will not work**
- pass a Server Component as a child or prop of a Client Component
    
    ```jsx
    'use client';
    export default function Page() {
      return (
        <ClientComponent>
          <ServerComponent />
        </ClientComponent>
      );
    }
    ```
    

## Usage

- Add interactivity and event listeners (`onClick()`, `onChange()`, etc)
- Use State and Lifecycle Effects (`useState()`, `useReducer()`, `useEffect()`, etc)
- Use browser-only APIs
- Use custom hooks that depend on state, effects, or browser-only APIs