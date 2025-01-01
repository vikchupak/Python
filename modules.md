- Any `.py` file is a module.
- No explicit export. Everything in a module is exported: Functions, Variables, Classes, Nested imports, Executable code (such as calculations or function calls at the top level)
  - Limiting What Gets Exported
    ```python
    # example.py
    __all__ = ['area_of_circle']  # Only `area_of_circle` is exported

    PI = 3.14159
    
    def area_of_circle(radius):
        return PI * radius ** 2
    
    def perimeter_of_circle(radius):
        return 2 * PI * radius
    ```
    ```python
    # main.py
    from example import *

    print(area_of_circle(5))  # Works
    print(perimeter_of_circle(5))  # Raises an ImportError
    ```

### **2. Importing Modules**

#### **Basic Import**
```python
# Importing the built-in math module
import math

print(math.sqrt(16))  # Output: 4.0
```

#### **Importing Specific Components**
```python
# Importing only the sqrt function from the math module
from math import sqrt

print(sqrt(25))  # Output: 5.0
```

#### **Renaming (Aliasing) a Module**
```python
# Using an alias for the math module
import math as m

print(m.pi)  # Output: 3.141592653589793
```

---

### **3. Types of Modules**

1. **Built-in Modules**  
   These are part of the Python standard library and are available by default. Examples include `math`, `os`, `sys`, `random`, etc.

   ```python
   import os
   print(os.name)  # Outputs the name of the operating system
   ```

2. **Third-Party Modules**  
   These are modules created by others and are available through the Python Package Index (**PyPI**). You can install them using `pip`.

   ```bash
   pip install requests
   ```

   ```python
   import requests
   response = requests.get("https://api.github.com")
   print(response.status_code)  # Output: 200
   ```

3. **Custom Modules**  
   You can create your own modules by writing Python code in a `.py` file.

   **example_module.py:**
   ```python
   def greet(name):
       return f"Hello, {name}!"
   ```

   **main.py:**
   ```python
   import example_module

   print(example_module.greet("Alice"))  # Output: Hello, Alice!
   ```

---

### **4. Module Search Path**
When you import a module, Python searches for it in the following order:
1. The current directory.
2. Directories listed in the `PYTHONPATH` environment variable.
3. Standard library directories.
4. Installed third-party modules (via `site-packages`).

You can see the search path using `sys.path`:
```python
import sys
print(sys.path)
```

---

### **5. Organizing Code with Modules**
For larger projects, you can organize related modules into a **package**. A package is a directory containing an `__init__.py` file (can be empty).

**Example Directory Structure:**
```
my_project/
    my_package/
        __init__.py
        module1.py
        module2.py
```

**Importing from a Package:**
```python
from my_package import module1
module1.some_function()
```

---

### **6. Reloading a Module**
If you modify a module during runtime, you can reload it without restarting the Python interpreter:
```python
import importlib
import example_module

# Reload the module
importlib.reload(example_module)
```
