## Static Site Generation (SSG)

In production, the page HTML is generated when you run `next build`. This HTML will then be reused on each request. It can be cached by a CDN.

### page content depends on external data

-  getStaticProps

```jsx
export async function getStaticProps({params}){ 

  return {
      props: {}
	  /* 
	  redirect: {
		 destination: '/no-date'
	  }
	  
	  notFound: true
	  
	  revalidate: 10
	  */
  }
}
```

### page paths depend on external data

-  getStaticPaths

```js
export async function getStaticPath(){
	return {
		paths: [
			{ params: { id: '1'} }, 
			{ params: { id: '2'} }, 
			{ params: { id: '3'} }
		],
		
		// true | false | blocking
		fallback: false // means other routes should 404
	};
}
```

## Server Side Rendering (SSR)

If a page uses Server-side Rendering, the page HTML is generated on each request.

- getServerSideProps

```jsx
export async function getServerSideProps(context) {
  const { params, res, res } = context

  return {
   props: {}
  }
}
```