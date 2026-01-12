# Class

Owner: Edwin

```tsx
class Person<T> { 
	private name: T; 
	constructor(name: T) { 
		this.name = name; 
	} 
	print() { 
		console.log(this.name); 
	} 
} 

const p1 = new Person<string>('a'); 
const p2 = new Person<number>(1);
```


```tsx
class User {
  private readonly email: string;
  password: string;

  constructor(email: string, password: string) {
    this.email = email;
    this.password = password;
  }
}
```