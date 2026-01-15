# getServerSideProps

```jsx
export default function Page({ data }) {
  // Render data...
}

// This gets called on every request
export async function getServerSideProps() {

  // Fetch data from external API
  const res = await fetch(`https://.../data`)
  const data = await res.json()

  // Pass data to the page via props
return {
    props: { data },
    // revalidate: 60,
    // notFound: true,
    // redirect: "/no-data"
  };
}

```