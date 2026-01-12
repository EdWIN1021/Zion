

```jsx
fetch("https://restcountries.eu/rest/v2/name/china")
  .then((res) => {
    if (res.ok) {
      return res.json();
    } else {
      throw new Error(res.status);
    }
  })
  .then((data) => console.log(data))
  .catch((err) => console.log(err));
```

```jsx
const res = await fetch("http://localhost:3000/api/v1/auth/tokens", {
  headers: {
    "Content-type": "application/json",
    Accept: "application/json",
    Authorization: "Bearer token",
  },
});
```