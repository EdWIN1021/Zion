# State

Owner: Edwin

<aside>
💡 renders are not triggered immediately, but scheduled for when the JS engine has some free time. There is also batching of multiple setState calls in event handlers.

</aside>

## Batching

- the process of grouping multiple state updates together and then applying them in a single re-render cycle.

![Screenshot 2023-11-11 at 9.28.21 AM.png](State%208c5c5130e544442686f4765e876d54ff/Screenshot_2023-11-11_at_9.28.21_AM.png)

![Screenshot 2023-11-11 at 9.33.03 AM.png](State%208c5c5130e544442686f4765e876d54ff/Screenshot_2023-11-11_at_9.33.03_AM.png)