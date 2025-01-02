Python provides several ways to unpack values from different data structures like tuples, lists, dictionaries, and more. Here's a comprehensive list of all unpacking methods in Python:

---

### **1. Tuple/Sequence Unpacking**
Unpacking values from a tuple, list, or any iterable into variables.

```python
# Tuple unpacking
a, b, c = (1, 2, 3)
print(a, b, c)  # Output: 1 2 3

# List unpacking
x, y, z = [4, 5, 6]
print(x, y, z)  # Output: 4 5 6

# String unpacking (as an iterable)
p, q, r = "ABC"
print(p, q, r)  # Output: A B C
```

---

### **2. Extended Iterable Unpacking**
Using the `*` operator to capture remaining values during unpacking.

```python
a, *b, c = [1, 2, 3, 4, 5]
print(a)  # Output: 1
print(b)  # Output: [2, 3, 4]
print(c)  # Output: 5
```

- **With Strings:**
  ```python
  first, *middle, last = "Python"
  print(first, middle, last)  # Output: P ['y', 't', 'h', 'o'] n
  ```

---

### **3. Nested Unpacking**
Unpacking values within nested tuples or lists.

```python
(a, (b, c)) = (1, (2, 3))
print(a, b, c)  # Output: 1 2 3

# With lists
[x, [y, z]] = [10, [20, 30]]
print(x, y, z)  # Output: 10 20 30
```

---

### **4. Dictionary Unpacking**
Using the `**` operator to unpack key-value pairs.

#### Function Arguments:
```python
def greet(name, age):
    print(f"Hello {name}, you are {age} years old.")

person = {"name": "Alice", "age": 30}
greet(**person)  # Output: Hello Alice, you are 30 years old.
```

#### Merging Dictionaries:
```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}

merged = {**dict1, **dict2}
print(merged)  # Output: {'a': 1, 'b': 3, 'c': 4}
```

---

### **5. Iterating with Unpacking**
Unpacking values during iteration (e.g., tuples in lists).

```python
pairs = [(1, 'one'), (2, 'two'), (3, 'three')]

for number, name in pairs:
    print(number, name)
# Output:
# 1 one
# 2 two
# 3 three
```

---

### **6. Starred Expressions in Iteration**
Use starred expressions for flexible unpacking in loops.

```python
data = [(1, 2, 3), (4, 5), (6, 7, 8, 9)]

for a, *b in data:
    print(a, b)
# Output:
# 1 [2, 3]
# 4 [5]
# 6 [7, 8, 9]
```

---

### **7. Unpacking Return Values**
Unpacking multiple values returned by a function.

```python
def get_coords():
    return (10, 20)

x, y = get_coords()
print(x, y)  # Output: 10 20
```

---

### **8. Ignoring Values with `_`**
Use `_` as a placeholder to ignore values you don't need.

```python
a, _, c = (1, 2, 3)
print(a, c)  # Output: 1 3

# Ignore multiple values
x, *_ = [10, 20, 30, 40]
print(x)  # Output: 10
```

---

### **9. Unpacking in List Comprehensions**
Unpack values while generating lists.

```python
pairs = [(1, 'one'), (2, 'two'), (3, 'three')]

# Extract the first elements
numbers = [num for num, _ in pairs]
print(numbers)  # Output: [1, 2, 3]
```

---

### **10. Starred Unpacking in Function Calls**
Unpacking arguments with `*` for positional arguments and `**` for keyword arguments.

```python
def add(a, b, c):
    return a + b + c

args = [1, 2, 3]
print(add(*args))  # Output: 6

kwargs = {"a": 1, "b": 2, "c": 3}
print(add(**kwargs))  # Output: 6
```

---

### **11. Merging Lists with `*`**
Unpacking lists into a new list.

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

merged = [*list1, *list2]
print(merged)  # Output: [1, 2, 3, 4, 5, 6]
```

---

### **12. Unpacking in `zip()`**
Combining unpacked iterables with `zip()`.

```python
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']

zipped = zip(list1, list2)
print(list(zipped))  # Output: [(1, 'a'), (2, 'b'), (3, 'c')]
```

---

### **Summary**
Python supports unpacking in various ways:
1. Tuple/sequence unpacking
2. Extended unpacking (`*`)
3. Nested unpacking
4. Dictionary unpacking (`**`)
5. Iteration unpacking
6. Starred expressions in iteration
7. Ignoring values with `_`
8. Return value unpacking
9. Function arguments unpacking (`*` and `**`)
10. Merging lists or dictionaries with `*` or `**`

Each unpacking method allows for clean, concise, and readable handling of data in Python.
