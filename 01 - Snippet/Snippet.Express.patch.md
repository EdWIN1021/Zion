# patch

Owner: Edwin

<aside>
💡 partial modifications

</aside>

```jsx
app.patch('/api/v1/tours/:id', (req, res) => {
		//do something
  res.status(200).json({
    status: 'success',
    data: {
      tour: 'updated',
    },
  });
});
```