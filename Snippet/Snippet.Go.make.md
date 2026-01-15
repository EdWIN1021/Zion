This creates an `int` slice with a length of 5 and a capacity of 5

```go
x := make([]int, 5)
```


This creates an `int` slice with a length of 5 and a capacity of 10.

```go
x := make([]int, 5, 10)
```

---


The length of 6 and a capacity of 10 

- the capacity was doubled as soon as the sixth element was appended

```go
x = append(x, 10)
```