# post

Owner: Edwin

```jsx
const res = await fetch("http://localhost:3000/api/v1/auth/login", {
      method: "POST",
      headers: {
        "Content-type": "application/json",
        Accept: "application/json",
        Authorization: "Bearer token",
      },
      body: JSON.stringify({ username: "edwin", password: "123" }),
    });
```