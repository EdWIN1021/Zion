# async

Owner: Edwin

```jsx
(async () => {
  try {
    const res = await fetch("https://restcountries.eu/rest/v2/name/china");
    const data = await res.json();
    if (res.ok) {
      console.log(data);
    } else {
      console.log(res);
    }
  } catch (err) {
    throw new Error(err);
  }
})();
```