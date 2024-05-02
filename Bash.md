--------------------------------------------------------------------------------
# Learn Shell Scripting - Fundamentals of Bash 4.4 : (Variables or constants) #
* Cheat-Sheet from https://ss64.com/bash/syntax-brackets.html
## Interesting commands (move to appropriate sections when comfortable) ##
```
  uname                      |
  lsof                       |
  netstat                    |
                             |
  return name of parent dir  | (basename $(dirname $$PWD)
                             |
  run a command periodically | watch
  to watch changes           |
                             |
  Open an editor to run a    | ctrl+x+e
  command                    |
                             |
  Create a fast ram disk     | mkdir -p /mnt/ram
                             | mount -t tmpfs tmpfs /mnt/ram -o size=2048M
                             |
  Fix a long command         | fc
                             |
  Create a tunnel with ssh   | (local port 3337 -> remote host's 127.0.0.1 on port 6379, connect using credentails root@emkc.org)
                             | ssh -L 3337:127.0.0.1:6379 root@emkc.org -N
                             |
  Intercept stdout and log   | cat file | tee -a log | cat > /dev/null
  to file                    |
                             |
  Exit terminal but leave    | disown -a && exit
  all processes running      |
```
## The set command 
```
  Description                | The set command is used to change the values of
                             | shell options and display variables in Bash
                             | scripts. It can also be used to debug Bash scrips,
                             | export values from shell scripts, terminate
                             | programs when they fail, and handle expressions
                             |
  -e (stop on error)         | When a query returns a non-zero status, the -e
                             | flag stops the script
                             |
  -C (type of write protect) | The -C flag ensures that we cannot overwrite an
                             | existing file with the same name
                             |
  -f (stop globbing)         | The -f prevenst us from using wildcards to search
                             | for filenames or strings
                             |
  -x (type of debuggin)      | The -x parameter is used when debugging scripts
                             | to determin the output of individual commands
                             |
  -a (var and func export)   | This flag can be used to export variables or
                             | functions
                             |
  -u                         | This flag is used to ensure that Bash does not
                             | overlook the non-existent variables in our script
                             | as in normal circumstances, Bash ignores unassigned
                             | variables
                             |
  +[argument]                | Running a set command with the +[argument] unsets
                             | the option's functionality, in essense, nullifying
                             | the effect of the -[argument] option
                             |
  -b                         | It is used to notify of job termination immediately.
                             |
  -h                         | It is used to save the location of commands where
                             | they looked up.
                             |
  -k                         | It is used to place all assignment arguments in
                             | the environment variable of a command, except
                             | those that precede the command name.
                             |
  -m                         | It is used to enable Job control.
                             |
  -n                         | It is used to read commands.
                             |
  -o                         | It is used for option-name.
                             |
  -p                         | It is used to disable the processing of the '$
                             | ENV' file and import shell functions. It is
                             | turned on whenever the real and effective user
                             | ids do not match. Turning off this option may
                             | cause the working uid and gid to be set as the
                             | authorized uid and gid.
                             |
  -t                         | It is used to exit from the command after
                             | executing one command.
                             |
  -u                         | It is used to treat unset variables as an error
                             | when substituting.
                             |
  -v                         | It is used to print shell input lines.
                             |
  -x                         | It is used to print commands and their arguments
                             | in a sequential way (as they are executed).
                             |
  -B                         | It is used to perform brace expansion by the Shell.
                             |
  -C                         | It is used to disallow existing regular files to
                             | be overwritten by redirection of output.
                             |
  -E                         | It is used if the ERR trap is inherited by the
                             | shell functions.
                             |
  -H                         | It is used to enable style history substitution.
                             | By default, it is on when the shell is interactive.
                             |
  -P                         | It is used if we do not want to follow symbolic
                             | links when executing commands.
                             |
  -T                         | If this flag is set, the DEBUG trap is inherited
                             | by the shell functions.
``` 
## Variables
```
  set                        | Displays all shell variables and function
                             |
  env                        | Displays only environment variables
                             | (i.e. variables with -x attribute set)
                             |
  $$ or ${...}               | Reference a value stored in a variable
                             |
  ...  or $(...)             | Execute command(s) and return the output as input
                             | for another command
  $((...)) or $[...]         | Perform an Arithmetic operation on the contents of
                             | variables and retun its results
                             |
  $?                         |"Return" the exit value of the previously executed
                             | command
                             |
  $0                         | Name of the command being executed
  $#                         | Number of command arguments
  $*                         | All command arguments
  $1, $2, ... $N             | Value of the corresponding argument
  $$                         | Process ID of the current shell
                             |
Interactively (from cli)     |
  !:0, !:1, !:2, etc         | returns portions of the previous command
```
## Variable Expansion
```
  To reference the value     | echo $variable | echo ${variable}
  of a variable (parameter)  |
                             |
  set the first letter of    | echo ${variable,}
  the referenced value to    |
  lowercase                  |
                             |
  set the whole value to     | echo ${variable,,}
  lowercase                  |
                             |
  set the first letter of    | echo ${variable^}
  the referenced value to    |
  uppercase                  |
                             |
  set the whole value to     | echo ${variable^&}
  uppercase                  |
                             |
  return the length of a     | echo ${#variable}
  parameter                  |
                             |
  Substring expansion        | ${parameter:offset:length}
```

## Command Substitution
```
  Retrieve the result of     | $(command)  -> uses parenthesis
  one or more commands       |
```

## Brace Expansion
```
  Expand string lists        | echo {a,19,z,barry,42}         <- the comma
                             | echo {jan,feb,mar,apr,may,jun}    separated values
                             |                                   must not contain
                             |                                   spaces
                             |
  Expand range lists         | {start..end..jump}   <- can only work with direct
                             | echo {1..10}            sequence of characters
                             | echo {10..1}
                             | echo {a..z}
                             | echo {1..1000..3}
                             | echo {01..12}        <- can add leading zeros
```

## commands to grokk
```
  find                       | find <search path> -name "*name-of-files*"
                             |   -iname  -> case insensitive
                             |
  cut                        | cut --delimiter=" " --fields=1
                             |
```

## Group and expand expressions
```
  Group commands - subshell  | ()
                             | Grouping a list of commands in parentheses
                             | causes them to be executed as if they were a single
                             | unit. When commands are pre grouped redirections
                             | can be applied to the entire command lits. for
                             | example, the output of all the commands in the list
                             | can be redirected to a single stream
                             |
  Double Parenthesis         | (()) is for arithmetic operation
                             |
  Single Square Brackets     | [] is the syntax for the POSIX *test*
                             |
  Double Square Brackets     | [[]] is the syntax for the bash conditional
                             |      (similar to *test*, but more powerfull)
                             |
  Current shell - group comm | {}
                             |
  Command substitution       | $(command(s))
                             |
  parameter substitution     | ${parameter(s)}
                             |
                             |
  Alternate explaination     |
                             |
    Single Brackets []       | Single Brackets are used for comparison operations.
                             | In the past *[* was  a command line the Unix test
                             | command
                             |
    Double brackets [[]]     | Double brackets are also used for comparisons, but
                             | they expose a richer syntax which enables more
                             | testing and comparison operations
                             |
    Single parenthesis ()    | Single parenthesis call a sub-shell
                             |
    Double parenthesis (())  | Double parenthesis are used for arithmetic                             |
                             |
    Single Braces {}         | Single Braces can be used to:
                             |   * Unambiguously identify variables
                             |   * Define a sequence of commands for the current
                             |     shell context
```

## Top level directorie
```
  /bin/                      | Contains essential binaries used by normal users
  /boot/                     | Contains files used in the boot process: kernel initramfs, bootloader
  /dev/                      | Contains special files used to access devices
  /etc/                      | Default location for software configuration files
  /home/                     | Contains the home directories for normal users
  /lib/                      | Contains system libraries
  /lib64/                    | Contains 64bit system libraries
  /media/                    | Removable devices such as USB and DVDs can be found here
  /mnt/                      | Empty by default, can be used to mount other filesystems
  /opt/                      | Directory where optional software can be installed
  /proc/                     | Directory where information about proccesses is stored
  /root/                     | The home directory of the root users
  /run/                      | Contains variable data about run-time data. different each boot
  /sbin/                     | Contains essential system binaris used by administrative users
  /srv/                      | Director to place data to be served by the server
  /sys/                      | Contains information about a the system, such as drivers and kernel features
  /tmp/                      | Dir intended for temporary files, often cleared on reboot
  /usr/                      | Contains non-essential files and binaries as read-only user data
  /var/                      | Contains varialble files, such as logs
```

## Understanding the Linux
```
 Permissions Scheme          |   id, touch, chmod, umask, chown, chgrop, sudo,
                             |   useradd, groupad, mkdir, and su
```

## Advanced permissions
```
                             | Other file attribtes include immutable undeletable,
                             | append only, and compress
                             |
                             | commands are:  lsattr and chattr
```                            
## Special file permissions
```
                             | SUID = 4, SGID = 2, Sticky bit = 1
                             |      | Files                       | Directories
                             |--------------------------------------------------
                             | SUID | Files are executed with the | does nothing
                             |      | permissions of the owner,   |
                             |      | regardless of which user    |
                             |      | executes it.                |
                             |--------------------------------------------------
                             | SGID | Files are executed with the | Files that are created in this
                             |      | permissions of the group,   | director get the same group as
                             |      | regardless of which user    | The directory
                             |      | executes it                 |
                             |--------------------------------------------------
                             |sticky| does nothing                | User can only delete their own
                             |bit   |                             | files within this directory. see
                             |      |                             | the /tmp/ director for its most
                             |      |                             | famous use.
```

## Process Control
```
  Stop long running process  | ctrl-c
                             |
  Suspend long running procs | ctrl-z
```

## evaluating math, dealing with numbers
```
 $(( numeric_variable + 1 ))
```

## User input
```
  Arguments and parameters   | when executing a script interactively, an
                             | argument is any "word" entered after the name of
                             | script. eg.
                             |   > bash ./script01.sh arg01 agr02 arg03
                             |
                             | the parameters which are used to reference
                             | these arguments within the script are $1, $2, $3
                             | respectively
                             |
  Requesting user input      | read
  read                       | While during the execution of a script, user
                             | can be asked with the read command
                             |
                             | read -p "text added as a prompt" var_assigned
                             |
  defaule variable set with  | $REPLY
  read                       |
                             |
  testing for default        | [[ -z ${test_var} ]]; then read -p "assign test_var" test_var
```
## Tests and return values
```
  test                       | the test command is used to check file types and
                             | compare values
                             |
                             | test -d /tmp/temp_dr  # use to check if file is dir
                             |
  test shorthand             | [[ -d /tmp/temp_dir ]] # [ ] can also be used
                             |
  $?                         | immediately after any command is run from bash (spawed bash)
                             | the spawed bash returns a success code for the run command
                             | to its parent bash (parent shell), assigned to the
                             | variable "$?" this variable can be used to make
                             | decisions for error handling and such
                             |
                             | [[ -d /tmp/temp_dir ]]
                             | [[ $? -ne 0 ]]; then echo "the Previous command was unsuccessful"
                             |
  $#                         | this varialbe is used to give the value of the
                             | number of arguments given to a script
                             |
                             | [[ $# -ne 3 ]] || { echo "this script needs 3 arguments" }
                             |
                             |
  Testing script             | When running a script you can give bash the "-x"
    bash -x ./some_script    | Argument and it will output every line run with
                             | all variables and expression substituted -- great
                             | for bug trackng
```

## Regular expressions
  * [Regular Expressions](programmingConcepts/re)

## Globbing ##
```
    Match zero or more times | *
                             |
    Any character once       | ?
                             |
    Any of a group of        | [abcde]
    one or a group of chars  |
```

## egrep ##
```
  ?                          | matches a repeat of the previous character zero or more times
  +                          | Matches a repeat of the previous character one or more times
  {n}                        | Matches a repeat of the previous character exactly n times
  {n,m}                      | Matches a repeat of the previous character between n and n times
  {,n}                       | Matches a repeat of previous character n or fewer times
  {n,}                       | Matches a repeat of the previous character n or more times
  (xx|yy)                    | Alternation character, allows us to fine xx OR y in the search
                             | pattern (great for patters with more than one character,
                             | otherwise, [xy] notion would suffice)
```

## sed
```
  Search and replace         | s/ (beginning of string)
                             | sed 's/wicked/stupid/'
                             | note: by default, sed only replace the first
                             | instance of each word for each line.
                             | sed does not match only on whole words, but also
                             | partial words.
                             |
  Global action              | /g (end of string)
                             | sed 's/wicked/stupid/g'
                             |
  Operation by line number   | 'n,n{option}'
                             | sed '1,2s/wicked/stupid/g'
                             |
  In-place (chages the file) | -i / --in-place
                             | sed -i 's/wicked/stupid/g' file.txt
                             |
  in-place change and backup | -i'file_extension' {pattern}
                             | -i'.bak' 's/wicked/stupid/g' file.txt
                             |
  Line delete                | sed 'd' | '/word/1d'  --< deletes line where word appears
                             |
  Line print                 | sed '/ERROR/p' will print two lines if default
                             | behavior is not surpressed (-n)
                             |
  quiet (surpresses default) | -n --quiet
    print behavror           |
                             |
  Run multi script on one    | -e
  stream                     |
```

## Conditional Operators
```
  and                        | &&
                             |
  or                         | ||
```

## Conditional Testing and Scripting Loops ##
```
  While loop                 | while true; do
                             | done
                             |
  Until loop                 | until [[ ${counter} -gt 9 ]]; do
                             | done
                             |
  for in loop                | for word in ${words}; do
                             | done
                             |
  for in range               | for counter in (1..10); do
                             | done
                             |
                             | for letter in (a..z); do
                             | done
                             |
                             | ((;;)); do  <-- infinite loop
                             | done
                             |
  for (traditional) loop     | for ((counter=0; counter<=10; counter++)); do
                             | done
Globbing and the loop        |
  looping through files in   | for file in $(ls /var/log/*.log); do
  a directory with glob      | done
                             |
  Break                      | break (default) <-- break out current loop
                             | break 1         <-- break out current loop
                             | break 2         <-- break out current loop and enclosing loop
                             |
  Continue                   | skip current iteration of loop, continue to next
```

## Using Pipes and Redirection
```
  File descriptors           |
    standard input stream    | stdin (default binding) /dev/fd/0
    standard output stream   | stdout (default )       /dev/fd/1
    standard error stream    | stderr (default)        /dev/fd/2
                             |
                             |
    redirect stdin           | <          (<0)
                             |
    redirect stdout overwrite| >          (1>)
    redirect stdout append   | >>         (1>>)
    redirect stderr overwrite| 2>
    redirect stderr append   | 2>>
    redirect both            | (bash 3.x) 2>&1
                             | (bash 4.x ~>) &>
                             |
  Special devices            |
                             | /dev/null    -> output send here dissappears
                             | /dev/zero    -> outputs null characters (fallocate --length 1024 {filename} same)
                             | /dev/random  -> only generates when there is enough "entropy"
                             | /dev/urandom -> better for scripting
                             |
  Command substitution       | Evalutates a command or list of commands, its result can be used
                             | as an argument for other commands
                             | $()
                             |
  Process substitution       | Evaluates a command or a list of commands, its result can be referenced
                             | as a file to for other commands
                             | <()
                             |
  Pipes                      | Connects the standard output of one command to the standard input of
                             | another
                             | |
                             |
    redirect output & error  | |&
                             |
  Here docs                  | << {end identifier} --> cat << EOF
    these are used to supply |
    commands with multi      | {end identifier}
    multi lines              |
                             |
    variables are interpola- | cat << 'EOF' --> variables are not interpolated
    ted, but you can surpres-|
    se this by quoting the   |
    end identifier           |
                             |
  Here strings               | <<< # used to send a string to a command which normaly only takes
                             |     input from stdin

```

## Functions 
```bash
  Covered commands: top, free declare, case, rev, return
  Function declarations      | function_name() {
                             |   Indented-commands
                             | }
                             |
                             | function function_name() {
                             |   intended-commands
                             | }
                             |
  Scope                      |
    define local variables   | local function_variable = 'test'
                             |
  Case statement             | case ${color} in
                             |   red)
                             |     <expressions>
                             |     ;;
                             |   blue)
                             |     color_code='blue'
                             |   *();;
                             |     color_code='default'
                             |
  Scope                      |
    define local variables   | local function_variable = 'test'
                             |
  Case statement             | case ${color} in
                             |   red)
                             |     color_code='red'
                             |   blue)
                             |     color_code='blue'
                             |      *)
                             |     color_code='default'
```

## Scheduling and Logging
```
  Commands: at, wall, atq, atrm, sendmail, crontab, alias
    Syntax for the crontab   | <timestamp> command
                             |
    <timestamp>              | 1. Minute-of-the-hour
                             | 2. Hour-of-the-day
                             | 3. Day-of-the-week
                             | 4. Month
                             | 5. Day-of-the-week
                             |
                             | In any of these values, we can substitute a number
                             | for a wildcar, which indeicates all values
                             |
                             | Crontab syntax     Semantic meaning
                             | 15 16 * * *        Every day at 16:15
                             | 30 * * * *         ddJK:WQJ
                             |
```

## Command line switches
```bash
  Filtering command line     | #!/bin/bash
  switches with case statment| echo
  (only checking the first   | while [ -n "$1" ]
   argument)                 | do
                             |   case "$1" in
                             |     -a) echo "Found the -a option" ;;
                             |     -b) echo "Found the -b option" ;;
                             |     -c) echo "Found the -c option" ;;
                             |     *) echo "$1 is not an option" ;;
                             |   esac
                             | shift
                             | done
                             |
  Switches with case statment|#!/bin/bash
  (checking all arguments)   |
                             |while [ -n "$1" ]
                             |do
                             |  case "$1" in
                             |    -a) echo "Found the -a option";;
                             |    -b) parm="$2"
                             |      echo "Fount the -b option, with parameter value $parm"
                             |      shift ;;
                             |    -c) echo "Fount the -c option";;
                             |    --) shift
                             |      break ;;
                             |    *) echo "$1 is not an option";;
                             |  esac
                             |  shift
                             |done
                             |count=1
                             |for param in "$@"
                             |do
                             |  echo "Parameter #$count: $param"
                             |  count=$(( $count + 1 ))
                             |done
```

### Common command line switches
```
   -a: List all objects.
   -c: Make a count.
   -d: Specify directory.
   -e: Expand the object.
   -f: Specify the file from which to read data.
   -h: Display command help.
   -i: Ignore case.
   -l: Perform full format data output.
   -n: Use non-interactive (batch) mode.
   -o: Allows you to specify the file to which you want to redirect the output.
   -q: Execute the script in quiet mode.
   -r: Process folders and files recursively.
   -s: Execute the script in silent mode.
   -v: Execute verbose output.
   -x: Exclude object.
   -y: Answer "yes" to all questions.
``` 
