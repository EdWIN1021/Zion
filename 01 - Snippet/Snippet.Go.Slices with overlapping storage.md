```go
x := []string{"a", "b", "c", "d"}
y := x[:2]

fmt.Println(cap(x), cap(y))


y = append(y, "z")

// [a b z d]
fmt.Println("x:", x)

// [a b z]
fmt.Println("y:", y)
```