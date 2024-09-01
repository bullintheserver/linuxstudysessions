---
title: "Topic 3"
layout: default
---

**LINKS**
- [**TOPIC 1:** The Linux Community and a Career in Open Source](https://bullintheserver.github.io/linuxstudysessions/topic1/1_1.html)
- [**TOPIC 2:** Finding Your Way on a Linux System](https://bullintheserver.github.io/linuxstudysessions/topic2/2_1.html)
- [**TOPIC 3:** The Power of the Command Line](https://bullintheserver.github.io/linuxstudysessions/topic3/3_1.html)
- [**TOPIC 4:** The Linux Operating System](https://bullintheserver.github.io/linuxstudysessions/topic4/4_1.html)
- [**TOPIC 5:** Security and File Permissions](https://bullintheserver.github.io/linuxstudysessions/topic5/5_1.html)

# Topic 3
The Power of the Command Line

## 3.1
Archiving Files on the Command Line  
Weight: 2 

### Introduction
- Compression
    - Reduces space consumption
    - Reduces data transfer size on networks
- Lossless
    - Can be uncompressed back to original
- Lossy
    - Cannot be recovered
    - Often used when:
        - Quality loss is imperceptible for humans
        - Space is more valuable than quality
        - Quality is irrelevant to context
- Linux compression tools
    - Lossless
        - `bzip2` (`.bz`)
        - `gzip` (`.gz`, `.z`, `.tgz` for `tar`)
        - `xz` (`.xz`)
    - Each tool uses a different algorithm
        - Won't work interchangeably
    - Incl. special versions of common tools
        - `cat`, `grep`, `diff`, `less`, `more`
        - `gzip` tools prefixed with `z`
            - e.g. `zcat`, `zgrep`, etc.
        - `bzip2` prefixed with `bz`
        - `xz` prefixed with `xz`
- Archiving tools
    - Used to bundle files/dirs. into single file
    - Common uses:
        - Backups
        - Bundled source code
        - Data retention 
    - Compression capabilities of archivers range from:
        - Optional
        - Default
        - Not included

### tar
- `tar`
    - Stands for *tape archive*
    - Most common Linux archiver
    - On it's own manages but does not compress
    - Files known as *tar balls*
- `-c` option
    - Creates new archive file
- `-f` option
    - Specifies the next input is name of file
    - Can include path
    - Without path, will place in current location
- Final arguments
    - After location and name
    - Paths to files/dirs to be included
- `-t` option
    - Lists contents of an archive
- `-v`
    - Verbose mode
    - Displays operations and names of files
- `-x`
    - Extracts files from archive
    - Can be used to extract single file from within archive
        - Use path and filename
- `-u`
    - Updater, appends does not overwrite 
    - Add files to existing uncompressed `tar` archive
    - Will cause error if attempted with compressed `tar`
- Compression calls as options
    - `bzip2`
        - `-j`
        - e.g. `tar -cjf file.tar.bz2 bigfile1`
    - `xz`
        - `-J` 
        - e.g. `tar -cJf file.tar.xz bigfile1`
    - `gzip`
        - `-z`
        - e.g. `tar -czf file.tar.gz bigfile1`
    - Remember to always add correct file extensions

### zip
- Windows compatibility 
    - `tar` applications uncommon in Windows
    - Use ZIP files for Windows interaction 
- ZIP files
    - Is an archive file
    - Similar to compressed `tar` file
    - `zip` & `unzip` will work on Linux CLI 
    - `-r` recursion needed to include directory contents
    - `-f` freshen
    - `#` 
        - Regulates speed of compression
        - `-1` fastest (least compression)
        - `-9` slowest (most compressed)
        - `-6` default level 

## 3.2
Searching and Extracting Data from Files  
Weight: 3 

### Lesson 1

#### I/O Redirection 
- *stdin*
    - Channel 0
    - Standard input
    - Considered to be keyboard
- *stdout*
    - Channel 1
    - Standard output
    - Considered screen
- *stderr*
    - Channel 2
    - Default redirects error outputs
        - For command
        - For programs 
        - Input/output can be redirected 
- Redirection of command components 
    - Transmit information to command
    - Redirect output to file
    - Redirect from or to command via text file
- `>`
    - Redirect output to file
    - Follow will name of file
    - Will create non-existent file
    - Will overwrite existing file
- `>>`
    - Appends and returns carriage to next line
    - Will not overwrite file
    - Can create new file
    - Follow with desired file name
- `2>`
    - Redirects just error messages
    - Follow with desired file name
    - useful for creating error logs
- `2>>`
    - Append error message
    - Same rules as `>>`
- `/dev/null`
    - Use with caution
    - Is a *bit bucket*
    - Unwanted output can be piped here
    - Data sent to `/dev/null` is discarded 
    - Provides no data when read from
- `<` 
    - Input data to a command from file
    - `cat < filename.txt`
    - Used with commands that don't accept file arguments
        - e.g. `tr -d "s" < filename.txt`
            - Deletes the letter "s" out of filename.txt 
- `<<`
    - *Here document*
    - Represents block of code/text which can be redirected to the command or interactive program
    - Different types of scripting languages can take input directly from CLI without using text files
    - Will present you with lines you can return in without submission
    - Submit by entering name given after `<<` followed by return carriage 
    - Can be combined with other redirection
        - e.g. `cat << inthehat > inthehat.txt`
- `&>`, `&>>`
    - Combines channel 1 and channel 2 outputs 
    - Use same rules as `>` and `>>` but with the channels combined

#### Command Line Pipes 
- `|`
    - *Pipes*
    - Link commands directly
    - Avoids saving output then running separate command
    - First command output becomes second command input
    - Can be used in succession to continue filtering 
- `head`
    - Displays first 10 lines of text by default
    - `-n` specifies number of lines if desired
- `tail`
    - Displays last 10 lines of text by default
    - `-n` specifies number of lines if desired
- `more`
    - Allows for paging through files
- `less`
    - Allows for paging through files 
    - Can scroll forward and backward
    - More robust and faster than `more`
    - *Less is more*
        - Used to remember `less` has more functionality 
- `wc`
    - Counts lines, words, bytes
    - `-w` counts only words
    - `-l` counts only lines
    - `-c` counts only bytes
- `cut`
    - Prints selected parts of lines from FILE to standard output
    - `-f` specifies the field 
    - `-d` specifies how fields are to be defined
        - Delimiter
        - e.g. `/` will define fields as between each `/`S
- `tr`
    - Translates or deletes characters
    - `-d` specifies deletion
    - `-s` *squeeze repeats* 
        - Replace sequence of repeated characters with single occurrence 
- `sort`
    - Write sorted concatenation of FILE to standard output
    - `-f` ignores case
    - `-r` reverses output 

### Lesson 2

#### grep
- `grep`
    - *global regular expression print*
    - Searches within file for specified pattern
    - Outputs line containing pattern and highlights in red
- `-i`
    - Search case-insensitive 
- `-r` 
    - Recursive search through subdirectories 
- `-c` 
    - Counts number of matches 
- `-v` 
    - Inverts search
    - Prints lines that do not match
- `-E`
    - Turns on extended regular expressions
    - Needed by advanced meta-characters
        - e.g. `|`, `+`, `?`
    - Can also use `egrep`
        - Depreciated in some systems

#### Regular Expressions
- Extracts data by constructing patterns
- Commonly used within scripts or when programming
    - Often with high level languages: Perl, Python
- !!! Every character counts !!!
    - Pattern is written to match specific string
- Most patterns use normal ASCII symbols
    - Letters
    - Digits
    - Punctuation
    - Symbols
- Can also use Unicode

| Meta-Characters | Function |
|-----------------|----------|
| `.` | Match any single character (except newline) |
| `[abcABC]` | Match any one character within the brackets |
| `[^abcABC]` | Match any one character except the ones in the brackets |
| `[a-z]` | Match any character in the range |
| `[^a-z]` | Match any character except the ones in the range |
| `either\|or` | Find either of the listed strings |
| `^` | Start of a line |
| `$` | End of a line |
| `*` | Zero or more of the preceding pattern |
| `+` | One or more of the preceding pattern |
| `?` | Zero or one of the preceding pattern |

```
$ grep "^a" text.txt
ant
anvil
arachnid 

$ grep "a$" text.txt
santa
flora
fauna

$ grep -E "ab.+" text.txt
abcde
about
cab ride
```

- `sed`
    - Stream editor
    - Filters and transforms text
    - Can find and replace characters and sets of characters

## 3.3
Turning Commands into a Script  
Weight: 4 

### Lesson 1

#### Commands and PATH
- `which` 
    - Locates a command
    - `a` prints all matching pathnames of each argument
- `$PATH`
    - View with `echo $PATH`
    - Each location in $PATH is where shell expects to find a command
    - Delimited with `:`
- Calling written script
    - Ways to tell shell how to find script
        - Move script into one of the `$PATH` directories
        - Add current directory to `PATH`
        - Specify *current location* with `./` 
            - `$ ./new_script_name` 
- Permissions
    - `ls -l` to view permissions
    - e.g. `drwxrwxrwx`
    - First bit indicates file type
        - `-` (file)
        - `d` (directory)
        - `l` (that is a lower case L, for link)
    - The 9 other bits represent
        - 1. 1-3 = *User*
        - 2. 4-6 = *Group*
        - 3. 7-9 = *Other*
    - Possible bit options
        - 1. *Read*
        - 2. *Write*
        - 3. *Execute*
        - A dash (`-`) indicates lack of permissions
        - e.g. `w-x`, `wr-`. `--x`
    - Symbolic representation
        - `4` represents `r`
        - `2` represents `w`
        - `1` represents `x`
        - e.g. `r-x` = 5, `r--` = 4, `rwx` = 7
        - Full string is represented by 3 digits
            - e.g. `-rw-rw-r--` is a file represented by `664`
    - `chmod` changes file mode bits
        - `chmod +x new_script` 
            - Grants execute perms to all users
            - Poses security risk, use with caution
- Defining the Interpreter 
    - If Bash script is being written find path for Bash script using:
        - `which bash`
        - `/bin/bash`
- *Shebang*
    - `#!`
    - Gets placed on first line of script
    - Follow with absolute path
    - Determines type of interpreter to use
    - e.g. `#!/bin/bash`
    - Comment lines
        - Start with `#`
        - Leave explanatory comments 
    - Label your script
        - Use naming conventions 
        - Script might be `.txt` 
            - Rename to `.sh` for Bash
            - `.bash` also used
            - Improves organization, accuracy, speed

#### Common Text Editors
- *vi*
    - Installed by default on almost every Linux system
    - Spawned clone *vi IMproved* aka *vim*
    - Has CLI modes
        - Navigation mode
            - Keyboard letters used for navigation
        - Insert mode
            - `i` to enter
            - Type normally here
            - `esc` to revert to navigation
        - Command mode
            - `:` to enter
            - Here is where you save, delete, quit, change
- *nano*
    - Newer 
    - Easier learning curve
    - No modes
    - Uses `Ctrl` to access tools

#### Variables
- Go to [Topic 2 | 2.1 | Lesson 2](https://github.com/bullintheserver/linuxstudysessions/blob/main/topic2.md#lesson-2)  
    - Refresher on:
        - Variables
        - Manipulating variables
- Tips
    - Variable names
        - Only alphanumeric characters or underscores
        - Case sensitive 
    - Substitution can also use `{}`
        - `${username}`
    - Variables in Bash have *implicit type*
        - They are considered strings
        - Makes math functions difficult 
            - Compared to languages such as C/C++
    - `"`
        - Weak, will still allow substitutions of symbols such as `$`
    - `'`
        - Strong, will convert meaningful symbols to plaintext 

##### Special Variables in Bash
| Variable | Description | Usage |
|----------|-------------|-------|
| $0 | The name of the script | `echo "This script is called $0"` |
| $1 - $9 | The first 9 arguments to the script | `echo "First argument: $1"` |
| ${10} and up | 10th argument and beyond | `echo "Tenth argument: ${10}"` |
| $# | The number of arguments passed to the script | `echo "Number of arguments: $#"` |
| $@ | All arguments passed to the script (preserves whitespace and quotes) | `for arg in "$@"; do echo "$arg"; done` |
| $* | All arguments passed to the script (does not preserve individual quotes) | `echo "All args: $*"` |
| $? | The exit status of the last command executed | `if [ $? -eq 0 ]; then echo "Success"; fi` |
| $$ | The process ID of the current script | `echo "PID: $$"` |
| $! | The process ID of the last background command | `echo "Last background PID: $!"` |
| $- | The current options set for the shell | `echo "Current shell options: $-"` |
| $_ | The last argument of the previous command | `echo "Last arg of previous command: $_"` |
| $IFS | Internal Field Separator | `IFS=':'; echo "IFS is now colon"` |
| $PATH | Executable search path | `echo "Current PATH: $PATH"` |
| $HOME | Home directory of the current user | `echo "Home directory: $HOME"` |
| $USER | Current user name | `echo "Current user: $USER"` |
| $HOSTNAME | The hostname of the machine | `echo "Hostname: $HOSTNAME"` |
| $RANDOM | Generates a random integer between 0 and 32767 | `echo "Random number: $RANDOM"` |
| $LINENO | The current line number in the script | `echo "This is line $LINENO"` |

#### Arguments
- Reminders
    - Arguments are words or values that follow a command 
    - Arguments provide input or instructions to the command
- Can be passed to the script upon execution
- Will modify how script behaves 

- Explanation and example
    - Below I run a script and pass three arguments
    - The script sets the username value as the third argument using a special variable listed above 
    - The script outputs the results using the special variable

```
$! /bin/bash
# This is a comment 

username=$3

echo "hello $username"
echo "number of arguments: $#"
```

```
$ ./bulli.sh cat dog bull
hello bull
number of arguments: 3
```
#### Conditional Logic in Bash

##### Common flags
| Flag | Description |
|------|-------------|
| `-eq`| Equal to |
| `-ne`| Not equal to |
| `-lt`| Less than |
| `-le`| Less than or equal to |
| `-gt`| Greater than |
| `-ge`| Greater than or equal to |
| `-z` | String is null (empty) |
| `-n` | String is not null (not empty) |
| `-d` | Directory exists |
| `-e` | File exists |
| `-f` | File exists and is a regular file |
| `-r` | File is readable |
| `-s` | File exists and is not empty |
| `-w` | File is writable |
| `-x` | File is executable |
| `-O` | File is owned by the current user |
| `-G` | File is owned by the current user's group |
| `!`  | Negates a test or exit status |
| `==` | Compares strings as true or false |

- Container
    - Logical outer container `if ... fi`
    - Test inner container `[]`
    - Nest conditionals if layered 
        - Use consistent nesting levels
    - Use spaces not tabs to ensure consistent display
    - Keep opening and closing keywords at same indent level

| Control Structure | Beginning Keyword | Ending Keyword | Function |
|-------------------|-------------------|----------------|----------|
| If statement| `if`  | `fi`     | Conditional execution of commands |
| Case statement    | `case`| `esac`   | Multi-way branch based on pattern matching |
| For loop    | `for` | `done`   | Iterate over a list of items |
| While loop  | `while`     | `done`   | Execute commands while a condition is true |
| Until loop  | `until`     | `done`   | Execute commands until a condition becomes true |
| Select loop | `select`    | `done`   | Create a numbered menu for user selection |
| Function    | `function` or name followed by `()` | `}`| Define a reusable block of code |


| Internal Keyword | Usage | Function |
|---------|-------|----------|
| in | `for item in list` | Separates loop variable from list in for loops |
| then | `if [condition]; then` | Marks beginning of code block in if statements |
| do | `for/while/until ...; do` | Marks beginning of loop body |
| elif | `elif [condition]; then` | Introduces additional conditions in if statements |
| else | `else` | Specifies actions when no conditions in if statement are met |
| break | `break` | Exits a loop prematurely |
| continue | `continue` | Skips rest of current loop iteration |
| select | `select var in list` | Generates a menu for user selection |


```
#!/bin/bash

# A simple script to greet a single user.

if [ $# -eq 1 ]
then
    username=$1

    echo "hello $username"
else
    echo "please enter only one argument"
fi
echo "number of arguments: $#"
```

```
$ ./bulli.sh cat dog bull
please enter only one argument
number of arguments: 3
```

```
$ ./bulli.sh bull
hello bull
number of arguments: 1
```
### Lesson 2

#### Exit Codes
| Exit Code | Name | Meaning |
|-----------|------|---------|
| 0 | Success | The command or script executed successfully |
| 1 | General error | Catchall for general errors or unspecified failures |
| 2 | Misuse of shell built-ins | Incorrect usage of shell built-in commands |
| 3-125 | Custom | Available for custom exit codes in scripts |
| 126 | Command invoked cannot execute | Permission problem or command is not executable |
| 127 | Command not found | Possible problem with $PATH or a typo |
| 128 | Invalid exit argument| Exit takes only integer args in the range 0-255 |
| 128+n | Fatal error signal "n" | Command terminated by signal n |
| 130 | Script terminated by Ctrl-C | Script terminated by user interrupt |
| 129 | SIGHUP (1) | Hangup detected |
| 130 | SIGINT (2) | Interrupt from keyboard (Ctrl+C) |
| 131 | SIGQUIT (3) | Quit from keyboard |
| 132 | SIGILL (4) | Illegal instruction |
| 133 | SIGTRAP (5) | Trace/breakpoint trap |
| 134 | SIGABRT (6) | Abort signal |
| 135 | SIGBUS (7) | Bus error |
| 136 | SIGFPE (8) | Floating point exception |
| 137 | SIGKILL (9) | Kill signal |
| 138 | SIGUSR1 (10) | User-defined signal 1 |
| 139 | SIGSEGV (11) | Invalid memory reference |
| 140 | SIGUSR2 (12) | User-defined signal 2   |
| 141 | SIGPIPE (13) | Broken pipe |
| 142 | SIGALRM (14) | Timer signal |
| 143 | SIGTERM (15) | Termination signal |
| 255 | Exit status out of range | Exit takes only integer args in the range 0-255 |

- Usage:
    - Numerical values
    - Indicator of execution status
    - Crucial to scripting, automation, error handling
    - Provides specific error information 
    - Useful in automated testing and deployment
    - Useful for debugging 
    - Facilitates communication between parent/child processes 
- `cat -n script_name.sh`
    - Use to print line numbers
    - Helpful for debugging
- Setting in scripts
    - `exit 0 # Success`
    - `exit 1 # Error`
    - *!Use at the end of the script!*
        - Using `exit` ends script
        - Ignores all after `exit`
- Checking exit code of last command
    - `echo $?`

#### Multiple Arguments 
- Array-like special variables
    - Allows script to operate on entire set of arguments at once
    - `$@`
    - `$*`
- Arrays within variables in Bash
    - Can be created with quotes and spaces
    - `FILES="sbin/1stfile sbin/2ndfile sbin/3rdfile"`
- Shifting
    - Use `shift` to shift parameters to the left by a specified number of positions 
        - Without arguments it is defaulted as `shift 1`
    - `$2` becomes `$1` and so on 
    - Original `$1` is discarded and is no longer accessible 
    - Will decrease value of `$#` by number of shifts
    - Updates `$@`, `$*`

#### *for* Loops and Loop Variables

##### Loop variables
- Control iteration of a loop
- Changes value with each iteration
- Conventions
    - Typically lowercase 
        - Distinguishes from
            - Constants
            - Environmental variables 
    - Always choose purpose-driven clear names
    - Avoid conflicting names with important shell variables
        - Can cause overriding 


##### Common loop variables
- Numeric iterators
    - Often named `i`, `j`, `k`
    - These variables increment numerically

```
for i in {1..5}
do
    echo "Iteration $i"
done
```

- File or item iterators
    - Variables like `file`, `item`, `element`
    - Represent each item in a list or array

```
for file in *.txt
do
    echo "Processing $file"
done
```

- Custom named variables
    - Any descriptive name
    - Represents items being iterated 

```
#!/bin/bash

# a friendly script to greet users

if [ $# -eq 0 ]
then
    echo "Please enter at least one user to greet"
    exit 1
else
    echo -n "hello $1"
    shift

    while [ $# -gt 1 ]; do
        echo -n ", $1"
        shift
    done

    if [ $# -eq 1 ]; then
        echo ", and $1"
    else
        echo "?"
    fi

    exit 0
fi
```

```
$ ./greeting.sh cat dog horse bull
hello cat, dog, horse, and bull
$
```

##### Using RegEx for Error Checking
Filtering for only letters example:
```
$ echo 4n1ml | grep "^[A-Za-z]*$"
$ echo $?
1
```

```
#!/bin/bash

# a friendly script to greet users

if [ $# -eq 0 ]
then
    echo "Please enter at least one user to greet."
    exit 1
else
    for username in $@
    do
        echo $username | grep "^[A-Za-z]*$" > /dev/null
        if [ $? -eq 1 ]
        then
            echo "ERROR: Names must only contains letters."
            exit 2
        else
            echo "Hello $username!"
        fi
    done
    exit 0
fi
```

```
#!

# Create a script that will take any number of
# arguments from the user, and print only those
# arguments which are numbers greater than 10

for i in $@; do
    echo $i | grep ^[0-9]*$ > /dev/null
    if [ $? -eq 0 ]; then
        if [ $i -gt 10 ]; then
            echo $i
        else
            echo $i > /dev/null
        fi
    fi
done
exit 0
```
---

