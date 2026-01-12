# TSharedPtr

Type: Class

<aside>
💡

- It is used to manage the lifetime of dynamically allocated objects in a way that helps prevent memory leaks and dangling pointers.
- `TSharedPtr` stands for "Thread-safe Shared Pointer," meaning it is safe to use across multiple threads.
</aside>

### **When to Use `TSharedPtr`**

Use `TSharedPtr` when you need shared ownership of an object, meaning multiple parts of your code need to access and manage the same object.

### **Reference Counting**

`TSharedPtr` uses reference counting to track how many shared pointers are referencing the same object. When the reference count drops to zero, the object is automatically deleted.

### **Thread Safety**

 The reference counting mechanism is thread-safe, making it suitable for use in multi-threaded environments.

### **Automatic Cleanup**

When the last `TSharedPtr` referencing an object goes out of scope or is reset, the object is automatically deleted.

```cpp
	TSharedPtr<FOnlineSessionSettings> SessionSettings = MakeShareable(new FOnlineSessionSettings());
```