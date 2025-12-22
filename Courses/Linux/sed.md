  Day 1: The Core Mission - Substitution
  The s (substitute) command is the heart of sed. Mastering it is the single most important step.

   * Concept: Find and replace text within a stream of text (like a file or command output).
   * Commands & Flags:
       * s/pattern/replacement/: Replaces the first occurrence of pattern on a line.
       * s/pattern/replacement/g: The g (global) flag replaces all occurrences on a line.
       * s/pattern/replacement/i: The i (case-insensitive) flag (a common GNU extension).
   * Example: To replace all instances of "red" with "blue" in a file:

   1     # This just prints to the terminal
   2     sed 's/red/blue/gi' filename.txt
   * Exercise: Take a text file and replace every instance of the word "the" (case-insensitively) with "THEE".

  Day 2: Power Through Precision - Addressing
  This is what makes sed a surgical tool. You'll learn to apply commands only to specific lines.

   * Concept: Restrict your commands to lines that match a certain address.
   * Types of Addresses:
       * Line Number: 3s/a/b/ (substitute on line 3 only).
       * Range: 5,10d (delete lines 5 through 10).
       * Pattern Match: '/ERROR/s/low/HIGH/' (on lines containing "ERROR", substitute "low" with "HIGH").
       * Negation: !d (don't delete, i.e., print).
   * Example: Delete all lines in a log file that contain "DEBUG":

   1     sed '/DEBUG/d' application.log
   * Exercise: From a file, print only the lines from 10 to 20 that contain the word "Complete". (Hint: you might need to
     chain two sed commands or use address grouping).

  Day 3: Making it Stick - In-Place Editing & Printing
  By default, sed just prints to your screen. Today you'll learn to save changes and control output.

   * Concept: Modify files directly and control what sed prints.
   * Flags & Commands:
       * -i: The in-place flag. This modifies the actual file. Use with caution!
           * sed -i 's/old/new/' file.txt (modifies file.txt)
           * sed -i.bak 's/old/new/' file.txt (modifies file.txt and creates file.txt.bak as a backup)
       * -n: The silent flag. sed will not print anything unless you explicitly tell it to.
       * p: The print command. Used with -n to print only specific lines.
   * Example: From a large config file, print only the lines containing "CACHE_SIZE":
   1     sed -n '/CACHE_SIZE/p' settings.conf
   * Exercise: Create a backup copy of a text file. Now, using sed -i, change every occurrence of "user" to your own name in
     the original file.

  Day 4: Line-Level Operations - Insert, Append, Change
  Go beyond just changing text within a line to manipulating entire lines.

   * Concept: Add, replace, or delete entire lines based on an address.
   * Commands:
       * i \: Insert text before the addressed line.
       * a \: Append text after the addressed line.
       * c \: Change (replace) the addressed line entirely.
   * Example: Find the line containing </head> in an HTML file and insert a stylesheet link right before it.

   1     sed '/<\/head>/i \    <link rel="stylesheet" href="style.css">' index.html
   * Exercise: Create a file with a list of tasks. Find the line containing "Task 3" and append a new line after it that says
     "Task 3a: Review".

  Day 5: The Magic of Regex - Capturing & Backreferences
  This is where your programming background gives you a huge advantage. You'll leverage regular expressions for complex
  transformations.

   * Concept: Use parentheses () to "capture" parts of your matched pattern and reuse them in the replacement string.
   * Key Syntax:
       * -E: Use extended regular expressions to avoid needing to escape characters like +, ?, ().
       * (): In your pattern, captures the text it encloses.
       * \1, \2: In your replacement, refers to the first and second captured groups.
       * &: In your replacement, refers to the entire matched pattern.
   * Example: Swap the order of "lastname, firstname" to "firstname lastname".

   1     # Input line: "Doe, John"
   2     sed -E 's/([a-zA-Z]+), ([a-zA-Z]+)/\2 \1/' names.csv
   3     # Output: "John Doe"
   * Exercise: You have a file with lines like IP: 192.168.1.1. Use a backreference to reformat these lines to be
     [192.168.1.1] is the IP address.

  Day 6: The Secret Weapon - Hold Space
  This is an intermediate topic, but understanding it is a key differentiator. Think of it as sed's clipboard.

   * Concept: The hold space is a separate, hidden buffer where you can temporarily save a line while you work on another.
   * Core Commands:
       * h: Hold. Copy the current line (pattern space) to the hold space, overwriting it.
       * g: Get. Copy the hold space back to the pattern space, overwriting it.
       * H: Hold (Append). Append the current line to the hold space.
       * G: Get (Append). Append the hold space to the current line.
   * Example: Move the first line of a file to the end.

   1     # 1h: on line 1, copy it to hold space
   2     # 1d: on line 1, delete it (so it's not printed)
   3     # $G: on the last line, append the hold space
   4     sed '1h; 1d; $G' file.txt
   * Exercise: Find a line containing the text "Summary" and move it to appear right after a line containing "Title". (Hint:
     you'll need h, G, and d).

  Day 7: Becoming a Scripter - Scripts & Review
  Combine your knowledge into reusable scripts.

   * Concept: For complex jobs, put your sed commands in a separate file.
   * Syntax:
       * -f: Execute a script file. sed -f transform.sed input.txt.
       * ;: Separate multiple commands on one line.
       * {}: Group multiple commands to be executed at a single address.
   * Example: Create a file named cleanup.sed with the following contents:
   1     # This is a sed script. Comments are allowed.
   2     # Remove trailing whitespace
   3     s/[ \t]*$//
   4
   5     # Delete all lines that are now empty
   6     /^$/d
      Now, run it:

   1     sed -f cleanup.sed document.txt
   * Exercise: Write a sed script that does three things:
       1. On lines containing "DEPRECATED", delete the entire line.
       2. On lines containing "FIXME", add [URGENT] to the beginning of the line.
       3. Globally replace "tmp" with "temporary".
      Run your script on a sample code file.
