# useReducer

Owner: Edwin

- A alternative way of setting state, ideal for complex state and related pieces of state.
- Stores related pieces of state in a state object.
- useReducer needs reducer function containing all logic to update state, separate state logic from component.
- reducer: pure function that takes current state and action, and returns the next state.
- action: object that describes how to update state.
- dispatch: function to trigger state updates, by sending actions from event handlers to the reducer.

![Screenshot 2023-11-12 at 10.49.41 AM.png](useReducer%20f5ff2c36ffc7410babec79c0adae494d/Screenshot_2023-11-12_at_10.49.41_AM.png)