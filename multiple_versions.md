# Install and manage multiple python versions

## Using update-alternatives (Manual, system-wide)

https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-an-ubuntu-20-04-server

```bash
sudo apt install python3
sudo apt install python3-pip
sudo apt install python3-venv
```

### Installing multiple `python3` versions via `apt`

You can install multiple versions of Python 3 via apt, but it depends on the versions available in your distribution's repositories.

### **1. Check Available Python Versions**
First, check which Python versions are available in your repository:
```bash
apt list python3.*
```

This will list all the `python3.x` versions and related packages available.

---

### **2. Install Multiple Python Versions**
You can install specific Python versions by installing their corresponding packages. For example:
```bash
sudo apt update
sudo apt install python3.10
sudo apt install python3.9
```

These versions will be installed alongside each other, and you can access them using their specific commands, such as:
```bash
python3.10 --version
python3.9 --version
```

---

### **3. Check Installed Versions**
List all Python versions installed on your system:
```bash
ls /usr/bin/python3*
```

This will show something like:
```plaintext
/usr/bin/python3
/usr/bin/python3.10
/usr/bin/python3.9
```

---

### **4. Change Default Python Version**
The default `python3` command usually points to a specific version (e.g., `/usr/bin/python3.10`). If you want to change this:

#### Use `update-alternatives`:
1. Add all installed Python versions to `update-alternatives`:
   ```bash
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 2
   ```

2. Configure the default version:
   ```bash
   sudo update-alternatives --config python3
   ```
   You'll be prompted to choose the version to use as the default.

---

### **5. Use Specific Versions When Needed**
Instead of changing the default, you can explicitly call the version you need:
```bash
python3.9 my_script.py
python3.10 my_script.py
```

---

### **6. Considerations**
- **Repository limitations**: The versions available in your distro's repositories might not always be the latest. For example:
  - Ubuntu 22.04 may have Python 3.10 as the default and older versions like 3.9 available.
  - If you need newer versions, you may need to use a **PPA** or compile from source.
- **Dependencies**: Be cautious when using different versions of Python for system tasks, as some critical tools may rely on the default Python version.

## Using `pyenv` (Recommended, user-specific in `~/.pyenv`)

`pyenv` is the closest equivalent to `nvm` for Python.

Installation on Ubuntu/Debian:

```bash
curl https://pyenv.run | bash
```

Add these lines to your shell configuration file `~/.bashrc`

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
```

### Commands

List the Python versions installed

```bash
pyenv versions
```

```bash
# Output
system (set by /home/user/.pyenv/version)
3.9.7
3.8.12
```

- `system`: Refers to the system-wide Python version installed on your machine.
- `*`: The currently active Python version. This is determined by pyenv global, pyenv local, or pyenv shell.

Set a global Python version
```bash
pyenv global 3.10.9
```

Set a local Python version for a project
```bash
pyenv local 3.9.7
```

Set a version for the current shell session
```bash
pyenv shell 3.8.12
```

# pyenv vs update-alternatives

***If multiple Python versions are installed via `apt` and NOT through `pyenv`, they will not be listed by the `pyenv versions` command.***
