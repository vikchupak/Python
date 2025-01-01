```python
try:
    num = 10 / 0 # This will raise a ZeroDivisionError
    # value = int("abc")  # This will raise a ValueError
    # raise Exception("Sorry, custom Error")
except ValueError as e:
    print(f"Invalid input! Please enter a number. {e}")
except ZeroDivisionError as e:
    print(f"Cannot divide by zero! {e}")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
else:
  print("No exceptions")
finally:
    print("Finally")
```
