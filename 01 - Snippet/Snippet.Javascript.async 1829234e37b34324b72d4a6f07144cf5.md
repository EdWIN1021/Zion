# async 1829234e37b34324b72d4a6f07144cf5

Owner: Edwin

# async

Owner: edwin S

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