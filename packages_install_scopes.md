# Scopes

- system wide
  - `sudo python3 -m pip install ansible`
    - install packages to system-wide dir
    - If no `sudo` used, then it defaults to user-spesific installation
- user-spesific
  - `python3 -m pip install --user ansible`
    - `--user` to install packages to `~/.local` directory. No `sudo` needed.
- project
  - Using `Virtual Environment`.
  - If venv active, no explicit `python3 -m pip` needed.

`python3 -m pip`

The command python3 -m pip uses Python's -m option to run the pip module as a script.

`pip` is tied to a specific Python interpreter because it is installed as part of that Python installation's environment and operates within the same directory structure. Here's how it works:

---

### **1. `pip` is a Python Package**
- When you install `pip`, it is added as a package to the **site-packages** directory of a specific Python interpreter.
  - For example, in a Python 3.10 installation:
    ```
    /usr/lib/python3.10/site-packages/pip/
    ```
- The `pip` command is just a shortcut that calls this package.

---

### **2. `pip` Binaries**
- When you install Python, a corresponding `pip` executable is created, usually in the same directory as the Python executable.
- For example:
  - Python executable: `/usr/bin/python3.10`
  - `pip` executable: `/usr/bin/pip3.10`

- The `pip` executable is essentially a wrapper script that invokes the `pip` package using the associated Python interpreter. For example:
  ```bash
  # Inside the pip3.10 script
  # Executes pip via Python 3.10
  /usr/bin/python3.10 -m pip "$@"
  ```

---

### **3. How `python3 -m pip` Ensures Correct Association**
When you run `python3 -m pip`:
1. Python uses its `-m` option to locate and execute the `pip` module installed in **that Python interpreter's environment**.
   - This ensures that the `pip` module being run is tied to the specific `python3` binary you invoked.
2. The packages installed using this `pip` are stored in the `site-packages` directory of the corresponding Python interpreter.

---

### **4. How Problems Arise with `pip` Commands**
If you run `pip3` directly:
- The system searches for the `pip3` executable in the `PATH` environment variable.
- If multiple Python installations exist, `pip3` might invoke a `pip` tied to a different Python version than you expect.

For example:
```bash
which pip3
# Output: /usr/local/bin/pip3
```
This might be tied to Python 3.8, even if your default `python3` is Python 3.10.

---

### **5. Tying `pip` to Python**
When you install Python, the `pip` module and binary are tied to that Python version because:
1. **Shared Installation Path:** `pip` is installed in the Python installation's directories.
2. **Executable Wrapper:** The `pip` binary calls the Python interpreter it was installed with.

---

### **Key Takeaway**
- Using `python3 -m pip` avoids ambiguity by explicitly invoking the `pip` module tied to a specific Python interpreter. It ensures that the correct `pip` and its associated environment are used.
