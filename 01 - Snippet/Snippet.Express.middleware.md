# middleware

Owner: Edwin

```jsx
app.use((req, res, next) => {
  console.log('Middleware');
  next();
});
```

## express.static

```jsx
// http://localhost:300/overview.html
app.use(express.static(`${__dirname}/public`));
```

## express.json

```jsx
// middleware for req.body or undefined
app.use(express.json()); 
```

## [morgan](https://www.notion.so/morgan-c16ea739c8db45c3ac3251b92a1a93e9?pvs=21)

```jsx
app.use(morgan('dev'));
```

## [router](router%208b028ac27e694fc1b851361a75a1e52a.md)

```jsx
app.use('/api/v1/[name]', [name]Router);
```

## router.param

```jsx
router.param('id', (req, res, next, value) => {
	 //value = id 
	console.log(value);
  next();
});
```