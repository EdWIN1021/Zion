# useFormStatus

```tsx
"use client";
import { useFormStatus } from "react-dom";

interface FormButtonProps {
  children: React.ReactNode;
}

const FormButton = ({ children }: FormButtonProps) => {
  const { pending } = useFormStatus();

  return (
    <button type="submit" disabled={pending}>
      {children}
    </button>
  );
};

export default FormButton;
```