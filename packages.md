- A module is a `.py` file
- A package is a collection of modules.
- A library is a collection of packages.

Packages repo https://pypi.org/ Like npm for js.

`pip` is a package manager for Python packages, or modules if you like.

```bash
# Without sudo, the following warning 'Defaulting to user installation because normal site-packages is not writeable'
pip install django
pip uninstall django
```

By default, `pip` installs packages into the `site-packages` directory of your Python installation.

```bash
On Ubuntu
~/.local/lib/python3.10/site-packages
```

To install packages locally/specifically for a project, `virtual environment` is used. See https://github.com/VIK2395/Python/blob/main/init_project.md
