```typescript
interface UserPayload {
  id: string;
  email: string;
}

declare global {
  namespace Express {
    interface Request {
	  //add new property to express Request interface
	  currentUser?: UserPayload;
	}
  }
}
```