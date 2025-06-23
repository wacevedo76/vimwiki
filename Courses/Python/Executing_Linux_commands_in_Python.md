* [Table of Contents](./index.md)

## Executing Linux Commands in Python
Python provides the `subprocess` module to execute system commands within a script.

**Example: Running a Shell Command**

```python
import subprocess

## Running the 'ls' command
result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
print(result.stdout)
```

**Example: Running a Command with Elevated Privileges**

```python
import subprocess

# Running 'sudo apt update' (requires user input for password)
subprocess.run(["sudo", "apt", "update"])
```
**Example: Capturing and Handling Return Codes**

When executing a subprocess, you can capture its return code to handle errors appropriately.

```python
import subprocess

result = subprocess.run(["ls", "non_existent_directory"], capture_output=True, text=True)

if result.returncode == 0:
    print("Command executed successfully:")
    print(result.stdout)
else:
    print("Error occurred:")
    print(result.stderr)
```

**Example: Capturing Output Before Checking Status**

You can capture and process the output before checking the return code:

```python
import subprocess

process = subprocess.Popen(["ls", "-l"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
out, err = process.communicate()

if process.returncode == 0:
    print("Command output:")
    print(out)
else:
    print("Error output:")
    print(err)
```
