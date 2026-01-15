```ad-important
Points to an object of type T on the heap
It is unique
Cannot be assigned or copied
Can be moved
When the pointer is destroyed, what it points to is automatically destroyed 
```


```cpp
#include <memory>
using namespace std;

unique_ptr<int> p1 { new int {100} };
unique_ptr<int> p1 = make_unique<int>(100);

unique_ptr<Account> p1 = { new Account {"Larry"} };
unique_ptr<Account> p1 = make_unique<Account>("Curly", 5000);

auto p1 = make_unique<Player>("Hero", 100, 100);

p1.get();   // 0x12345
p1.reset(); // nullptr

unique_ptr<Test> t1 { new Test {100} };
unique_ptr<Test> t3;
t3 = move(t1);
```