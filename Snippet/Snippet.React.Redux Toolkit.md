# Redux Toolkit

Owner: Edwin

# Toolkit

## 目录

- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)
- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)
- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)
- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)
- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)
- [Redux](../Redux%207ec3f31a0d6e4b47a823d090261417dd.md)

## Install

---

```bash
npm install @reduxjs/toolkit react-redux//oryarn add @reduxjs/toolkit react-redux
```

## Store

---

> 📌src/store.js
> 

```
import { configureStore } from "@reduxjs/toolkit";
import fooReducer from "./features/fooSlice";

export const store = configureStore({
  reducer: {
    foo: fooReducer,
  },
});
```

## Provider

---

> src/index.js
> 

```
import { Provider } from "react-redux";
import { store } from "./store";

<Provider store={store}>
    <App />
</Provider>
```

## Slice

---

> 📌src/features/fooSlice.js
> 

```
import { createSlice } from '@reduxjs/toolkit'

const initialState = {
    data: ''
}

export const fooSlice = createSlice({
    name:'foo',
    initialState,
    reducers:{
        fn:(state, actions) => {
            this.state.data = actions.payload.data
        }
    }
})

export const { fn } = fooSlice.actions

export default fooSlice.reducer
```

## Dispatch

---

```
import { useDispatch } from "react-redux";
import { fn } from '../../fooSlice'

const dispatch = useDispatch();

dispatch(fn({data:'data'}));
```

## State

---

```
import { useSelector } from "react-redux";

const data = useSelector(state => state.foo.data);
```