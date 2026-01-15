# dynamic route

Owner: Edwin

```jsx
app.get('/api/v1/tours/:id', (req, res) => {
  // req.params = id
  res.status(200).json({
    status: 'success',
    data: {},
  });
});
```