# `pyenv`

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

**If multiple Python versions are installed via `apt` and NOT through `pyenv`, they will not be listed by the `pyenv versions` command.**

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
