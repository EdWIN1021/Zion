```tsx
import Link from 'next/link' 

<Link href='/'>Home</Link> 

<Link href='/about'>About</Link> 

{/* cannot go back */} 
<Link replace href={`/blog/${post.slug}`}>{post.title}</Link> 

<Link href="/#dashboard" scroll={false}>To Dashboard</Link> 

<Link href={{ pathname: "/clients/[id]", query: { id: client.id } }}>
	{client.name} 
</Link>
```