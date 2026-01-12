# API Routes

- Any file inside the folder pages/api is mapped to /api/* and will be treated as an API endpoint instead of a page. (server-side only)

```tsx
import type { NextApiRequest, NextApiResponse } from 'next'
type ResponseData = { message: string }
export default function handler(
  req: NextApiRequest,
  res: NextApiResponse<ResponseData>
) {
  // req.cookies | req.query | req.body  // res.status | res.json | res.send | res.redirect(307, '/') | res.revalidate  if (req.method === 'POST') {
    // Process a POST request  }
  else {
   // Handle any other HTTP method  }
  res.status(200).json({ message: 'Hello from Next.js!' })
}
```