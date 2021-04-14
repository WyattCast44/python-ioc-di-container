# Python IOC Container

This is a simple inversion of control (IOC) container written in python with zero dependencies.

# Usage

```python
from .Container import Container

class MyClassContract:
    pass

class MyClassConcrete:
    pass

c = Container()

# Basic binding
# So now whenever i ask the container for a MyClassContract
# it will give me an instance of MyClassConcrete
c.bind(MyClassContract, MyClassConcrete)

a = c.make(MyClassContract)

# Binding an instance
# So now whenever i ask the container for a MyClassContract
# it will give me the existing instance of MyClassConcrete
b = MyClassConcrete()

c.instance(MyClassContract, b)

d = c.make(MyClassContract)

# Binding an singleton
# So now whenever i ask the container for a MyClassContract
# it will create an instance and give me the the same instance of MyClassConcrete
c.singleton(MyClassContract, MyClassConcrete)

e = c.make(MyClassContract)
f = c.make(MyClassContract) # same instance as e
```