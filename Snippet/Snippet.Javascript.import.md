# import

Owner: Edwin

---

## default export

---

```jsx
import person from "./person.js";
```

## named export

---

```jsx
import { funA, funB } from "./utils.js";
```

## alias

```
import { funA as FUNA } from "./utils.js";
```

## *

```
import * as utils from "./utils.js";

utils.funA();
utils.funB();
```