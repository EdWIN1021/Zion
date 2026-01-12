## Event Loop

1. **Call Stack:**
    
    - JavaScript is single-threaded, meaning it can execute only one operation at a time in a single call stack.
    - The call stack is a data structure that keeps track of the function calls. When a function is called, it is added to the top of the stack, and when the function is done, it is removed from the stack.
2. **Callback Queue:**
    
    - JavaScript can perform asynchronous operations, like making HTTP requests or handling user input. When these asynchronous operations complete, they generate events and place the associated callback functions in the callback queue.
3. **Event Loop:**
    
    - The event loop is a continuous process that constantly checks the call stack and the callback queue.
    - If the call stack is empty, the event loop takes the first function from the callback queue and pushes it onto the call stack to be executed.
4. **Microtasks and Macrotasks:**
    
    - In addition to the callback queue, JavaScript has two kinds of tasks: microtasks and macrotasks.
    - Microtasks (e.g., Promises, async / await ) are tasks with higher priority than macrotasks (e.g., setTimeout, setInterval, DOM events, Ajax, script). Microtasks are processed before the next macrotask in the event loop.