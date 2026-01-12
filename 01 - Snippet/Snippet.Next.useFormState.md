# useFormState

```tsx
"use client";
import { useFormState } from "react-dom";
import * as actions from "@/actions";

const [formState, action] = useFormState(actions.createSnippet, {
  message: "",
});

export async function createSnippet(
  formState: { message: string },
  formData: FormData
) {
  return { messgae:"error message" }
}
```