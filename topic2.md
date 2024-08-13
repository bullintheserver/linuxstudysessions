# Topic 2
Finding Your Way on a Linux System

## 2.1
Command Line Basics  
Weight: 3 

### Lesson 1

#### Shell
- Text mode program that reads user imput and interprets it as commands to the system
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
        - Options: `-l` is the swtich that modifies behavior
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
    - Revoke any speical meaning
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
        - Avaiable to current shell process only
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
- Remove variable using `unset` without `$` as it is now an argument
    - If `$` is used it resolves the variable to it's value instead of affecting the variable name 
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
    - Behaves as it pattern is surrounded by aserisks by default
        - Allows for substrings instead of exact filename
        - Recent files might not be found
            - Update database using `sudo updatedb`
- `find`
    - Searches directory tree recursively
    - Does not mantain a database like `locate`
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

### Files and Directories

#### Lesson 1

