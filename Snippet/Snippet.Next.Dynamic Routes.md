# Dynamic Routes

- A Dynamic Segment can be created by wrapping a folder’s name in square brackets: `[folderName]`
- Dynamic Segments are passed as the params prop to [layout](../File%20Conventions%20e4bfb7b688b94c84bb77fba29f1c324f/layout%2016bdabea80e546098c8beb8eda9d2b96.md), [page](../File%20Conventions%20e4bfb7b688b94c84bb77fba29f1c324f/page%20c86ed4f7ca444b6099d55edfbbe64200.md), route, and generateMetadata functions.

```tsx
export default function Page({ params }: { params: { slug: string } }) {
  return <h1>My Page</h1>;
}
```