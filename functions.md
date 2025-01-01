## pass by ref vs value

- Pass by ref list, dict, set, class instance(object), bytearray
- All other pass by value

## var scopes

- In python, threre is no var hoisting like in js.

Block Scope:

- Python uses **function-level scope** for variables, but blocks (like `if` or `for`) do not create their own scope.
- JavaScript has **block-level scope** with `let` and `const`, but `var` has function-level scope.

**In python, functions can accept other functions as arguments and return functions. High order functions.**

```python
def greet(name = 'Vasa', age = 20):
    print(f"Hello, {name}. You are {age} years old.")
    # return type <class 'NoneType'>

# Named arguments
greet(age = 46)
# Without explicit providing default arguments, python throws an error when the arguments are missing, unlike javascript
```

##  Func inside func

Python allows creating functions inside functions, a concept often referred to as nested functions or inner functions. These are functions defined within the scope of another function.

```python
def outer_function():
    print("This is the outer function.")

    def inner_function():
        print("This is the inner function.")

    inner_function()  # Calling the inner function

outer_function()
```

```python
def decorator(func):
    def wrapper():
        print("Something is happening before the function call.")
        func()
        print("Something is happening after the function call.")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

## Lambda Functions (Anonymous Functions)

A lambda function is a small, anonymous function defined with the lambda keyword. It’s often used for short operations, such as in functional programming scenarios.

```python
add = lambda x, y: x + y
result = add(5, 3)
print(result)  # Output: 8
```

lambda x, y: x + y: An anonymous function that adds two values
