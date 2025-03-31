# Python

Several common software platforms, 
including Python (a widely used programming language) 
are highly extensible by loading packages.

These packages can be loaded within the application itself,
or before the application is launched, using a package manager.

`pip` is the package installer for Python.
To load Python packages on Roar, use `pip` with the `--user` flag
(which directs Python to install the package for a single user):

```
pip install --user <package>
```

Sometimes, user python package libraries can become too large for storage in the home directory. 
To correct this issue, see [Quota issues in home](../handling-files/file-storage.md/#quota-issues-in-home).

