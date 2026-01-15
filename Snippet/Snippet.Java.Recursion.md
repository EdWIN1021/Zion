## Recursion

- When a method called itself, new local variable and parameters are allocated storage on the stack, and the method code is executed with these new local variables from the start.
- As each recursive call returns, the old local variables and parameters are removed from stack. and execution resumes at the point of the call inside the method.