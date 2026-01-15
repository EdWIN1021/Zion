# Error Controller

Owner: Edwin

<aside>
💡 err object contains the data which is passed by next() function

</aside>

```jsx
export const errorHandler = (
	err: any,
	req: Request,
	res: Response,
	next: NextFunction
) => {
	next();
};
```