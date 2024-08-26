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
    - Gets placed on first line of script
    - Determines type of interpreter to use
    - e.g. `#!/bin/bash`
    