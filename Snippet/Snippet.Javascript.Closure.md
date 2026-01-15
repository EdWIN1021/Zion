# Closure

Owner: Edwin

- 闭包让你可以在一个内层函数中访问到其外层函数的作用域
- 当外部的方法被执行之后, 内部的作用域不会被垃圾回收机制销毁
- 只要使用了回调函数，实际上就是在使用闭包

![Closure%207d360377d78947e88ae96937829242f2/closureimageimage_QFVU_iG4Vx.png](Closure%207d360377d78947e88ae96937829242f2/closureimageimage_QFVU_iG4Vx.png)

```jsx
function greet(whattosay) {   
	return function(name){       
		console.log(whattosay + ' ' + name)   
	}
}

greet('hi')('edwin')
```