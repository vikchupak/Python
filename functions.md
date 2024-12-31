Functions can accept other functions as arguments and return functions. High order functions.

```python
def greet(name = 'Vasa', age = 20):
    print(f"Hello, {name}. You are {age} years old.")
    # return type <class 'NoneType'>

# Named arguments
greet(age = 46)
```

## Lambda Functions (Anonymous Functions)

A lambda function is a small, anonymous function defined with the lambda keyword. It’s often used for short operations, such as in functional programming scenarios.

```python
add = lambda x, y: x + y
result = add(5, 3)
print(result)  # Output: 8
```

lambda x, y: x + y: An anonymous function that adds two values
