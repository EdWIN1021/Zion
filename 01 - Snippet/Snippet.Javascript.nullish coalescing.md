# nullish coalescing

Owner: Edwin

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