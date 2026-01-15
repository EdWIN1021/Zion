# Route Handler

```tsx
import { NextResponse } from 'next/server';

//get
export async function GET() {
  const res = await fetch('https://data.mongodb-api.com/...', {
    headers: {
      'Content-Type': 'application/json',
      'API-Key': process.env.DATA_API_KEY,
    },
  });
  const data = await res.json();

  return NextResponse.json({ data });
}

//Dynamic Route Segments with get request
export async function GET(request: Request, { params }:{ params: { slug: string }}) {
  const slug = params.slug;
    const res = await request.json();

  return NextResponse.json({ res });
}

//post
export async function POST() {
  const res = await fetch('https://data.mongodb-api.com/...', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'API-Key': process.env.DATA_API_KEY,
    },
    body: JSON.stringify({ time: new Date().toISOString() }),
  });

  const data = await res.json();

  return NextResponse.json(data);
}

```