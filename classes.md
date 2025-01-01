### **1. Defining a Class**
A class is defined using the `class` keyword. Here's the basic syntax:

```python
class ClassName:
    # Constructor (optional)
    def __init__(self, attribute1, attribute2):
        self.attribute1 = attribute1
        self.attribute2 = attribute2

    # Method
    def method_name(self):
        return f"Attribute1 is {self.attribute1}"
```

---

### **2. Creating Objects**
To create an object (instance of a class), simply call the class like a function:

```python
# Creating an object
obj = ClassName("value1", "value2")

# Accessing attributes and methods
print(obj.attribute1)  # Output: value1
print(obj.method_name())  # Output: Attribute1 is value1
```

---

### **3. Key Features of Classes**

#### **(a) Constructor (`__init__`)**
The `__init__` method initializes an object when it is created. It’s like a constructor in other programming languages.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p = Person("Alice", 30)
print(p.name)  # Output: Alice
print(p.age)   # Output: 30
```

---

#### **(b) Attributes**
Attributes are variables that belong to a class or an instance.

1. **Instance Attributes**: Defined inside the `__init__` method and are specific to each object.
2. **Class Attributes**: Shared across all instances of the class.

```python
class Example:
    class_attr = "Shared"

    def __init__(self, instance_attr):
        self.instance_attr = instance_attr

obj1 = Example("Instance1")
obj2 = Example("Instance2")

print(obj1.class_attr)  # Output: Shared
print(obj2.instance_attr)  # Output: Instance2
```

---

#### **(c) Methods**
Methods are functions defined within a class. 

1. **Instance Methods**: Operate on instance attributes and take `self` as the first parameter.
2. **Class Methods**: Operate on class attributes and use `@classmethod`. The first parameter is `cls`.
3. **Static Methods**: Don’t operate on class or instance attributes. Use `@staticmethod`.

```python
class Example:
    class_attr = "Class Attribute"

    def instance_method(self):
        return "Instance Method"

    @classmethod
    def class_method(cls):
        return cls.class_attr

    @staticmethod
    def static_method():
        return "Static Method"
```

---

### **4. Inheritance**
Python supports class inheritance, allowing one class to derive from another.

```python
class Parent:
    def greet(self):
        return "Hello from Parent!"

class Child(Parent):
    def greet(self):
        return "Hello from Child!"

c = Child()
print(c.greet())  # Output: Hello from Child!
```

- **Overriding**: Child classes can override methods from parent classes.
- Use `super()` to access the parent class’s methods.

---

### **5. Special Methods (Dunder Methods)**
Special methods (also called "magic methods") allow customization of behavior for built-in operations.

Examples:
- `__init__`: Constructor
- `__str__`: String representation
- `__len__`: Length of an object
- `__getitem__`: Item access in a custom way

```python
class Custom:
    def __init__(self, data):
        self.data = data

    def __str__(self):
        return f"Custom({self.data})"

obj = Custom([1, 2, 3])
print(obj)  # Output: Custom([1, 2, 3])
```

---

### **6. Encapsulation**
Encapsulation hides implementation details from the user. Use:
- **Private attributes**: Prefix with `__` (double underscore). Example: `self.__private_attr`
- **Protected attributes**: Prefix with `_` (single underscore). Example: `self._protected_attr`

```python
class EncapsulationExample:
    def __init__(self):
        self.public = "I am public"
        self._protected = "I am protected"
        self.__private = "I am private"
```

This is not syntax sugar. It really throws error.

---

### **7. Polymorphism**
Different classes can define methods with the same name, allowing flexibility in calling them.

```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

animals = [Dog(), Cat()]
for animal in animals:
    print(animal.speak())
```

---

### **8. Composition**
One class can contain an instance of another class as an attribute.

```python
class Engine:
    def start(self):
        return "Engine started"

class Car:
    def __init__(self):
        self.engine = Engine()

    def start(self):
        return self.engine.start()

car = Car()
print(car.start())  # Output: Engine started
```

---

### **9. Abstract Classes**
Python supports abstract classes using the `abc` module. These classes cannot be instantiated directly.

```python
from abc import ABC, abstractmethod

class AbstractExample(ABC):
    @abstractmethod
    def abstract_method(self):
        pass

class ConcreteClass(AbstractExample):
    def abstract_method(self):
        return "Implemented abstract method"

obj = ConcreteClass()
print(obj.abstract_method())  # Output: Implemented abstract method
```

### **10. Getters and Setters

```python
class Person:
    def __init__(self, name, age):
        self._name = name  # Private attribute (by convention)
        self._age = age    # Private attribute (by convention)

    # Getter for name
    def get_name(self):
        return self._name

    # Setter for name
    def set_name(self, name):
        self._name = name

    # Getter for age
    def get_age(self):
        return self._age

    # Setter for age
    def set_age(self, age):
        if age >= 0:
            self._age = age
        else:
            print("Age must be a positive number")

# Usage
person = Person("Alice", 25)

# Accessing private attributes using getters
print(person.get_name())  # Output: Alice
print(person.get_age())   # Output: 25

# Modifying private attributes using setters
person.set_name("Bob")
person.set_age(30)

print(person.get_name())  # Output: Bob
print(person.get_age())   # Output: 30
```
