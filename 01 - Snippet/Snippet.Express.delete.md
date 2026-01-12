# delete

Owner: Edwin

```jsx
app.delete('/api/v1/tours/:id', (req, res) => {
  res.status(204).json({
    status: 'success',
    data: null,
  });
});
```