* [Table of Contents](./index.md)

# Checking File Permissions in Linux
You can use the `os` module to check file permissions in Python.

**Example: Checking File Read/Write Permissions**
```python
import os

file_path = "sample.txt"

# Check if the file is readable
if os.access(file_path, os.R_OK):
    print(f"{file_path} is readable.")
else:
    print(f"{file_path} is not readable.")

# Check if the file is writable
if os.access(file_path, os.W_OK):
    print(f"{file_path} is writable.")
else:
    print(f"{file_path} is not writable.")
```

**Example: Using `stat` to Get File Permissions**
```python
import os
import stat

file_path = "sample.txt"
file_stat = os.stat(file_path)

# Convert mode to human-readable format
permissions = stat.filemode(file_stat.st_mode)
print(f"Permissions for {file_path}: {permissions}")
```

### Conclusion
Regular expressions provide a powerful way to process text data in files. By combining Python’s file handling capabilities with regex, you can efficiently search, extract, and modify text. Additionally, Python allows you to execute Linux commands and check file permissions, making it a versatile tool for system administration tasks.

