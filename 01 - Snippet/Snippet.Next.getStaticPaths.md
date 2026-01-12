# getStaticPaths

- fallback
    - false
        - Any paths not returned by **`getStaticPaths`** will result in a 404 page
    - true
        - The page will be built on-demand the first time a request is made, and the generated HTML will be cached for subsequent requests.

```tsx
export async function getStaticProps(context: GetStaticPropsContext) {
  const { params } = context;

  const res = await fetch(`path`);
  const data = await res.json();

  return { props: { data } };
}

export async function getStaticPaths() {
  return {
    paths: [
      {
				// onlyt this path generate at build time
        params: { userId: "1" }, 
      },
    ],
    fallback: true,
  };
}
```