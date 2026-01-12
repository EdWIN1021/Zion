# class

```python
class Circle():
    pi = 3.14
    def __init__(self, radius=1): #default value        self.radius = radius
        self.area = radius * radius * Circle.pi
    def get_circumference(self):
        return self.radius * self.pi * 2
c = Circle(30)
c.get_circumference()
```