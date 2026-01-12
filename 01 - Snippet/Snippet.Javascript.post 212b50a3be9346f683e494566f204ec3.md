# post 212b50a3be9346f683e494566f204ec3

Owner: Edwin

# post

Owner: edwin S

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