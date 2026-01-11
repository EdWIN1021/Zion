```ad-info
A type alias is a name that is a synonym for another type.
```


## typedef
```cpp
typedef double wages;   // wages is a synonym for double
typedef wages base, *p; // base is a synonym for double, p for double

typedef char *pstring;
const pstring cstr = 0;
const pstring *ps; //ps is a pointer to a constant pointer to char
```

## using
```cpp
using SI = Sales_Item; // SI is a synonym for Sales_item
```

