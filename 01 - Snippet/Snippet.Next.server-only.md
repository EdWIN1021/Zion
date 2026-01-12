# server-only

```bash
npm install server-only
```

```jsx
import 'server-only';

export async function getData() {
  let resp = await fetch('https://external-service.com/data', {
    headers: {
      authorization: process.env.API_KEY,
    },
  });

  return resp.json();
}
```