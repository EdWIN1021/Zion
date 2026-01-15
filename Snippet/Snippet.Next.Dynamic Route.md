# Dynamic Route

- Calling a dynamic function or referencing a dynamic variable when your route renders
    
    ```tsx
    cookie.set() cookie.delete()
    useSearchParamas() # searchParams prop
    ```
    
- Assigning specific route segment config options
    
    ```tsx
    export const dynamic = 'force-dynamic'
    export const revalidate = 0
    ```
    
- Calling fetch and opting out of caching of the response
    
    ```tsx
    fetch("...",{next:{revalidate: 0}})
    ```
    
- Using dynamic route
    
    ```
    /snippets/[id]/pages/.tsx
    /snippets/edit/[id]/pages/.tsx
    ```