* [Table of Contents](./index)

# File Processing with Regular Expressions in Python

## Introduction

File processing is a common task in programming, involving reading from and writing to files. When combined with regular expressions (regex), you can efficiently search, extract, and manipulate text data within files. Python provides powerful tools such as the re module for regex operations and built-in file handling capabilities.

## Opening and Reading Files

To process a file, you first need to open it in the appropriate mode. Here’s how you can read a file line by line:

```python
with open("sample.txt", "r") as file:
    for line in file:
        print(line.strip())  # Remove leading/trailing whitespace
```
## Using Regular Expressions for Pattern Matching

Python’s `re` module allows you to search for specific patterns within text. Common regex functions include:
* `re.search(pattern, string)`: Searches for the pattern in a string.
* `re.findall(pattern, string)`: Returns all occurrences of the pattern.
* `re.sub(pattern, replacement, string)`: Replaces occurrences of a pattern with a new string.

### Example: Finding Email Addresses in a File

```python
import re

pattern = r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'  # Email pattern

with open("data.txt", "r") as file:
    for line in file:
        matches = re.findall(pattern, line)
        if matches:
            print("Found emails:", matches)

```
## Writing to a File

You can write processed data to a new file using the w (write) or a (append) mode:
```python
with open("output.txt", "w") as file:
    file.write("This is a new file containing processed data.\n")

```
###Example: Extracting and Writing Phone Numbers
```python
pattern = r'\b\d{3}-\d{3}-\d{4}\b'  # Phone number pattern (e.g., 123-456-7890)

with open("contacts.txt", "r") as infile, open("phone_numbers.txt", "w") as outfile:
    for line in infile:
        matches = re.findall(pattern, line)
        if matches:
            outfile.write("\n".join(matches) + "\n")


## Conclusion

Regular expressions provide a powerful way to process text data in files. By combining Python’s file handling capabilities with regex, you can efficiently search, extract, and modify text. Experiment with different regex patterns to handle more complex text-processing tasks.
