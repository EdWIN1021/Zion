# middleware

```tsx
import type { NextRequest } from 'next/server'

export function middleware(request: NextRequest) {

  // This logic is only applied to /about }
  if(request.nextUrl.pathname.startsWith('/about')){}

  // This logic is only applied to /dashboard }
  if (request.nextUrl.pathname.startsWith('/dashboard')){}

```