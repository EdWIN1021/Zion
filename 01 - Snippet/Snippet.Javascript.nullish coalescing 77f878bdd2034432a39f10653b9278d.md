# nullish coalescing 77f878bdd2034432a39f10653b9278d8

Owner: Edwin

# nullish coalescing

Owner: edwin S

```jsx
const obj = undefined ?? {};
// obj => {}

const obj = null ?? {};
// obj => {}

const obj = 0 ?? {};      // 0  = false
// obj => 0

const obj = "" ?? {};     // "" = false
// obj => ""
```