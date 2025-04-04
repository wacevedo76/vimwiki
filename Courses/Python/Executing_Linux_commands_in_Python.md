* [Table of Contents](./index.md)

# Executing Linux Commands in Python

Python provides the `subprocess` module to execute system commands within a script.

**Example: Running a Shell Command**

```python
import subprocess

# Running the 'ls' command
result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
print(result.stdout)
```

**Example: Running a Command with Elevated Privileges**

```python
import subprocess

# Running 'sudo apt update' (requires user input for password)
subprocess.run(["sudo", "apt", "update"])
```
