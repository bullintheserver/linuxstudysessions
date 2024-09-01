---
title: "Topic 2"
layout: default
---

**LINKS**
- [**TOPIC 1:** The Linux Community and a Career in Open Source](https://bullintheserver.github.io/linuxstudysessions/topic1/1_1.html)
- [**TOPIC 2:** Finding Your Way on a Linux System](https://bullintheserver.github.io/linuxstudysessions/topic2/2_1.html)
- [**TOPIC 3:** The Power of the Command Line](https://bullintheserver.github.io/linuxstudysessions/topic3/3_1.html)
- [**TOPIC 4:** The Linux Operating System](https://bullintheserver.github.io/linuxstudysessions/topic4/4_1.html)
- [**TOPIC 5:** Security and File Permissions](https://bullintheserver.github.io/linuxstudysessions/topic5/5_1.html)

# Topic 2
Finding Your Way on a Linux System

## 2.1
Command Line Basics  
Weight: 3 

### Lesson 1

#### Shell
- Text mode program that reads user input and interprets it as commands to the system
- A few common shells
    - Bourne-again shell (Bash)
    - C shell (csh, tcsh, enhanced csh)
    - Korn shell (ksh)
    - Z shell (zsh)
- Bash
    - Most common on Linux
- Default prompt structure
    - `username@hostname currentdirectory _shell_type`
- Ubuntu, Debian GNU/Linux
    - Regular user
        - `carol@mycomputer:~$`
    - Superuser
        - `root@mycomputer:~#`
- CentOS, RHL
    - Regular user
        - `[dave@mycomputer~]$`
    - Superuser
        - `[root@mycomputer~]#`
- Components of structure
    - `username`
        - Name of user that runs the shell
    - `hostname`
        - Name of host on which shell runs
        - There is also a command `hostname`
            - Shows or sets system host name
    - `current_directory`
        - Directory shell is currently in
        - A `~` means shell is in current user's home directory
    - `shell_type` 
        - `$` indicates shell is run by regular user
        - `#` indicates shell is run by superuser `root`

#### Command line structure
- Basic structure
    - `command [option(s)...] [argument(s)...]
    - Example: `$ ls -l /home`
        - Command: `ls` is program that will be run
        - Options: `-l` is the switch that modifies behavior
        - Argument: `/home` is the additional data required, such as path or filename
    - `--help`
        - Use after command to display short overview of command

#### Command behavior types
- Internal
    - Part of shell itself
    - Main purpose is executing tasks inside the shell
- External
    - Reside in individual files
    - Usually binary programs or scripts
    - Uses the `PATH` variable to search for executable file
    - Users can create their own
- `type`
    - Follow with command to show type

```
$ type echo
echo is a shell builtin

$ type man
man is /usr/bin/man
```

#### Quoting
- Three types of quotes in Bash
    - Double quotes
    - Single quotes
    - Escape characters
- Double quotes
    - Text in between quote marks are regular characters
    - Special characters lose meaning
        - Except
            - `$`
            - `\`
            - `` ` ``
    - Although you could create filenames with spaces using double quotes, best practice is to use `_` or `.` as spacers instead

```
$ touch "new file"
vs
$ touch new_file
```

- Single quotes
    - No exceptions 
    - Revoke any special meaning
- Escape characters
    - Removes special meanings of characters
    - Placed before special character

```
tom@mycomputer:~$ echo I am $USER
I am tom
tom@mycomputer:~$ echo "I am $USER"
I am tom
tom@mycomputer:~$ echo 'I am $USER'
I am $USER
tom@mycomputer:~$ echo I am \$USER
I am $USER
```

### Lesson 2

#### Variables
- Pieces of storage for data
    - Such as text or numbers
    - Value can be accessed at a later time
    - Access by set name, even if content changes
    - Common tool in most programming languages
- Two types in most Linux shells
    - Local variables
        - Available to current shell process only
        - Not inherited by sub processes
    - Environment variables
        - Available in specific shell sessions and in sub processes spawned from that shell session
        - Can pass configuration data to commands which are run
        - Majority of enviro variables are in capital letters
            - e.g. `PATH`, `DATE`, `USER`
        - For example, a set of default enviro variables provide info about user's home directory 
        - Sometimes complete set of all enviro variables is referred to as the *environment*
        - `env` command displays all enviro variables 
- Variables are not persistent 
    - When shell closes, variables and contents are lost
    - Most shells provide config files that contain variables which are set on shell launch
    - If variable should be permanent, it must be added to config file

#### Manipulating variables 
- Set up local variable using `=`
- Access value using `$`
    - Tells Bash to expand the variable and use its value
- Remove variable using `unset` without `$` as it is now an argument
    - If `$` is used it expands the variable to it's value instead of affecting the variable name 

```
$ greeting=hello
$ echo $greeting
hello
$ unset greeting
```

- Use `export` to make variable available to subprocesses and make it an enviro variable

```
$ export greeting=hello
```

- Use environment variables in front of commands
    - Example
        - `TZ` holds timezone
        - `date` command displays date and time information

```
$ TZ='America/Los_Angeles' date
Sun July 4 12:12:12 PM PDT 2025
```

- `Path` 
    - Stores list of directories, separated by a colon, that contain executable programs eligible as commands from the Linux shell
    - Use `:` to append new directory to the variable
        - In example, `$PATH` is resolved as the current value, and the `:new_directory` is added on to the resolution using the setting function `=` 
    - Use `PATH` variable with caution
    - `which` can be used to locate executable files
    - Order of elements in `PATH` defines lookup order

```
$ echo $PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$ PATH=$PATH:new_directory
$ echo $PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:new_directory
$ which nano
/usr/bin/nano
```

- Command substitution
    - ``` var_name=`command [OPTION] path_here` ```

```
$ nr_files=`wc -l /etc/passwd`
$ echo $nr_files
100 /etc/passwd
```


## 2.2
Using the Command Line to Get Help  
Weight: 2

### Getting Help on the Command Line
- `/usr/share/doc/`
    - Stores most documentation of commands used by system 
    - Contains directory for most packages installed on system
        - Usually name of package and possibly version
        - Include a `README` OR `readme.txt` containing basic package documentation
        - Folder can also contain other documentation such as:
            - Changelog
                - Includes history of program in detail
            - Example configuration files
- `--help`
    - Follows command_name
    - Brief instructions on command usage
    - Good first try for learning parameters
- `man`
    - Manual page
    - Command to be explained added as argument
        - `man ls`
    - `q` quits manual page
    - Use `/` in front of word to search forward
    - Use `?` in front of word to search backward
    - Use `n` to jump to next match
- Each man page divided into max of 11 sections
    - Some sections are optional

| Section | Description |
|---------|-------------|
| NAME | Command name and brief description |
| SYNOPSIS | Description of the command's syntax |
| DESCRIPTION | Description of the effects of the command |
| OPTIONS | Available options |
| ARGUMENTS | Available arguments |
| FILES | Auxiliary files |
| EXAMPLES | A sample of the command line |
| SEE ALSO | Cross-references to the related topics |
| DIAGNOSTICS | Warning and Error messages |
| COPYRIGHT | Author(s) of the command |
| BUGS | Any known limitations of the command |

- There are 8 categories of man pages
    - Each man page belongs to exactly one category
    - Multiple categories can contain man pages with same name
    - You can specify category number
        - `man 1 passwd`, `man 5 passwd`


| Category | Description |
|----------|-------------|
| 1 | Executable programs or shell commands |
| 2 | System calls (functions provided by the kernel) |
| 3 | Library calls (functions within program libraries) |
| 4 | Special files (usually found in /dev) |
| 5 | File formats and conventions, e.g. /etc/passwd |
| 6 | Games |
| 7 | Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7), man-pages(7) |
| 8 | System administration commands (usually only for root) |
| 9 | Kernel routines [Non standard] |

- Info pages
    - More detailed than `man` pages
    - Formatted in hypertext 
    - Command to be explained added as argument
        - `info mkdir`
    - Read from file structured as nodes within a tree
    - Contains hyperlinks 
    - Use `?` for navigation instructions
- `locate`
    - Searches within a database
    - Outputs ever matching string
    - Supports wildcard and regular expressions use
    - Behaves as it pattern is surrounded by asterisks by default
        - Allows for substrings instead of exact filename
        - Recent files might not be found
            - Update database using `sudo updatedb`
- `find`
    - Searches directory tree recursively
    - Does not maintain a database like `locate`
    - Supports wildcards and regular expressions
    - Requires at least a path
        - `.` Searches current directory
        - `~` Searches user's home directory
    - Expressions can be added to filter 
        - e.g. `-name` 

```
$ find ~ -name thesis.pdf
/home/carol/Downloads/thesis.pdf
```

## 2.3
Using Directories and Listing Files  
Weight: 2  

### Lesson 1

#### Files, Directories, Naming

- Files
    - Contain data
        - Human readable text
        - Executable programs
        - Binary data
- Directories
    - Create organization within filesystem
    - Can contain
        - Files
        - Subdirectories
            - Has a *parent* / *child* relationship
- Naming
    - Case sensitive
    - Files and directories can contain
        - Upper case
        - Lower case
        - Numbers
        - Spaces
        - Special characters
        - Suffixes
            - .txt, .pdf, .jpg, etc.
            - Have no special meaning in Linux
            - There for human understanding

#### Navigating the Filesystem

- `pwd`
    - *Print working directory*
    - Can also be seen in command prompt before `$` or `#`
    - Always prints absolute path
        - Every step of path printed 
        - Always begins with a `/`
- `/`
    - Denotes relationships
    - Directory hierarchy read from left to right
    - Directories on right are subdirectories
    - Directories on left are parent directories
- `ls` 
    - Lists contents of current directory
    - Does not see parent or child directories by default
        - Must use modifier to see beyond current directory
- `cd` 
    - Changes directory
    - Can use absolute or relative path
        - Use `ls` to relative paths for current location
    - `cd ..` up a level
    - `cd /` root directory
    - `cd ~` home directory
    - `cd -` previous directory
    - `cd [path] && ls`
        - Goes to `path` and lists contents simultaneously
    - Can use relative paths 
        - Only has meaning in relation to current location


### Lesson 2

#### Home Directories
- Changes in root affect all users
- Changes in root require admin perms
- Home
    - Users separated into dedicated compartments 
    - Root responsible for utilities and maintenance 
- Terminal command prompt 
    - `user@hostname ~ $`
        - The `~` represents *home directory*
    - Users will always begin a new session in their home directory
    - `cd ~` or `cd` to jump to user `home`
    - Specify `home` of other users by placing username after tilde
        - `$ ls ~michael`
        - Must have permission

#### Hidden Files and Directories
- `ls -a`
    - Lists all, incl. hidden, files and directories
    - Hidden files and directories will always begin with a period `.`
        - `.` represents *current location*
        - `..` represents *parent directory*
    - By default, user's home includes many hidden files
        - Used to set user-specific config settings 
        - Should only be modified by experienced user
- `ls -l` 
    - Alias `ll`
    - `-l` creates a long list
    - Files and dirs. occupy one line
    - Additional info on each file and dir. is displayed
        - Permissions
        - Number of links to the file
        - Ownership
        - Size in bytes
        - Timestamp of last modification
        - Name

```
$ ls -l
-rw-r--r-- 1 user staff    3606 Jan 13  2017 report2018.txt
```

#### Additional `ls` Options

- `ls -lh` 
    - Combines *long list* with *human readable* 
- `ls -d */` 
    - `-d` option lists directories but not contents
    - `*/` shows only subdirectories and no files
- `ls -lt` 
    - Combines *long list* with sort by *modification time*
    - Most recent at top, oldest at bottom
- `ls -lrt` 
    - Same as above but with `r` *reverse* sort
- `ls -lX` 
    - Combines *long list* with sort by *file eXtension* 
- `ls -S` 
    - Sorts by *size*
    - Large to small 
    - Subdirectories not included in sort
- `ls -R` 
    - Displays *recursive* list
    - "Unfolds" or runs the "ls" command in each subdirectory 

## 2.4
Creating, Moving, and Deleting Files  
Weight: 2 

### Creating 

- Case sensitivity
    - Linux is case sensitive
    - Windows is not case sensitive 
- Directories
    - File used to organize files
    - Directories can hold other directories
- Files
    - Collection of data
        - Has a name
        - Has attributes
- `mkdir` 
    - Creates directories
    - Add `-p` or `--parents` option to create subdirectories simultaneously
- `find` 
    - Used to search for files and directories
    - Without options, returns listing of all files, directories, sub-dirs. of current directory
- `touch`
    - Followed by name will create empty file 
    - If ran on existing file, mod timestamp will update
- `cat` aka *concatenate*
    - Used to view contents of a file
    - Can merge files
        - `cat file1.txt file2.txt > file3.txt`
- `echo`
    - Displays text on the command line
    - If ran with an `>` *output redirect* it will write the text to a file
    - `>` will overwrite if file name already exists
    - `>>` appends text to the end of existing file

### Moving
- `mv`
    - Last argument is destination dir
    - Multiple files can be specified
    - ex: `mv file1 file2 dir1`
    - Can be used to rename
        - `mv dir1 dir2`

### Deleting
- `rm` can delete files and directories
    - Use `rm -r` to recursively remove nested directories
        - USE WITH CAUTION
        - `rm -ri` to prompt for confirmation before deletion
- `rmdir` will delete empty directories

### Copying
- `cp` copies files and directories
    - Use last argument as destination of copies
    - If last argument is a file, it will be overwritten 
    - Use `-r` for copying directories
        - Will also copy contents of directory

### Globbing
- Pattern matching language 
- `*` 
    - Matches any number of any characters
        - Includes no characters
- `?`
    - Matches any one character
- `[]`
    - Matches a class of characters 
        - `[:classname:]`
        - e.g. `ls file[[:digit:]]`
    - Both `[]` and `{}` will work with `ls` to display ranges
        - `ls file[1-3]` or `ls file{1..3}` 
    - Only `{}` will work with `touch` to write a range of individual files
        - `touch file{1..3}`
- Pattern matching characters can be mixed
    - `ls file[1-3]*`
- Must use `\` to escape these special meanings

| classname | description |
|-----------|-------------|
| [:alnum:] | Letters and numbers |
| [:alpha:] | Upper or lowercase letters |
| [:blank:] | Spaces and tabs |
| [:cntrl:] | Control characters, e.g. backspace, bell, NAK, escape |
| [:digit:] | Numerals (0123456789) |
| [:graph:] | Graphic characters (all characters except ctrl and the space character) |
| [:lower:] | Lowercase letters (a-z) |
| [:print:] | Printable characters (alnum, punct, and the space character) |
| [:punct:] | Punctuation characters, i.e. !, &, " |
| [:space:] | Whitespace characters, e.g. tabs, spaces, newlines |
| [:upper:] | Uppercase letters (A-Z) |
| [:xdigit:] | Hexadecimal numerals (usually 0123456789abcdefABCDEF) |

---