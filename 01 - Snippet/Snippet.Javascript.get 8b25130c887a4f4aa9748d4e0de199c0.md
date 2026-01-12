# get 8b25130c887a4f4aa9748d4e0de199c0

Owner: Edwin

# get

Owner: edwin S

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