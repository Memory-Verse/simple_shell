<p align="center">
  <img src="http://www.alxafrica.com/wp-content/uploads/2022/01/header-logo.png"
    alt="ALX Africa Logo">
  </p>


# C - Simple Shell

# Requirements

* Allowed editors: vi, vim, emacs
* All your files will be compiled on Ubuntu 20.04 LTS using gcc, using the options -Wall -Werror -Wextra -pedantic -std=gnu89
* All your files should end with a new line
* A README.md file, at the root of the folder of the project is mandatory
* Your code should use the Betty style. It will be checked using betty-style.pl and betty-doc.pl
* Your shell should not have any memory leaks
* No more than 5 functions per file
* All your header files should be include guarded
* Use system calls only when you need to (why?)


## More Info
# Output
Unless specified otherwise, your program must have the exact same output as sh `(/bin/sh)` as well as the exact same error output.
The only difference is when you print an error, the name of the program must be equivalent to your argv[0] (See below)
Example of error with sh:
```
$ echo "qwerty" | /bin/sh
/bin/sh: 1: qwerty: not found
$ echo "qwerty" | /bin/../bin/sh
/bin/../bin/sh: 1: qwerty: not found
$
Same error with your program hsh:

$ echo "qwerty" | ./hsh
./hsh: 1: qwerty: not found
$ echo "qwerty" | ./././hsh
./././hsh: 1: qwerty: not found
$
```
# List of allowed functions and system calls

***
* `access` (man 2 access)
* `chdir` (man 2 chdir)
* `close` (man 2 close)
* `closedir` (man 3 closedir)
* `execve` (man 2 execve)
* `exit` (man 3 exit)
* `_exit` (man 2 _exit)
* `fflush` (man 3 fflush)
* `fork` (man 2 fork)
* `free` (man 3 free)
* `getcwd` (man 3 getcwd)
* `getline` (man 3 getline)
* `getpid` (man 2 getpid)
* `isatty` (man 3 isatty)
* `kill` (man 2 kill)
* `malloc` (man 3 malloc)
* `open` (man 2 open)
* `opendir` (man 3 opendir)
* `perror` (man 3 perror)
* `read` (man 2 read)
* `readdir` (man 3 readdir)
* `signal` (man 2 signal)
* `stat` (__xstat) (man 2 stat)
* `lstat` (__lxstat) (man 2 lstat)
* `fstat` (__fxstat) (man 2 fstat)
* `strtok` (man 3 strtok)
* `wait` (man 2 wait)
* `waitpid` (man 2 waitpid)
* `wait3` (man 2 wait3)
* `wait4` (man 2 wait4)
* `write` (man 2 write)

# Compilation
## Your shell will be compiled this way:

`gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh`

# Project Layout

```
.
├── README.md
├── shell.h
├── main.c
├── prompt.c
├── tokenizer.c
.
.
.


## Function Prototypes.

The header file declares several function prototypes for the shell program, including:

`prompt()`: prints the shell prompt

`execute()`: executes a command with arguments

`get_line()`: Read input from the standard input. Custom getline().

`get_input()`: Retrieves user input from stdin. Uses getline().

`tokenize()`: parsing user input into arguments.

`handle_sigint()`: signal handler for SIGINT

`handle_sigstp()`: signal handler for SIGSTP

`handle_sigquit()`: signal handler for SIGQUIT

`check_for_builtin()`: checks if a command is a shell builtin

`shell_env()`: prints environment variables

`shell_setenv()`: sets an environment variable

`shell_unsetenv()`: unsets an environment variable

`shell_help()`: prints help information for the shell

`shell_cd()`: changes the current working directory

`shell_exit()`: exits the shell program with a status code

`_myenv()`: retrieves the value of an environment variable

`find_in_path()`: searches for a command in the directories specified by the PATH environment variable

`get_path()`: retrieves the PATH environment variable

`set_path()`: sets the PATH environment variable

`append_to_path()`: appends a directory to the PATH environment variable

`prepend_to_path()`: prepends a directory to the PATH environment variable

`free_error()`: frees memory allocated following system error

`free_tokens()`: frees memory allocated for tokens

`_puterror()`: prints an error message

`_puts()`: prints a string

`_atoi()`: converts a string to an integer

`_putchar()`: prints a character

`_strlen()`: gets the length of a string

`_strcmp()`: compares two strings

`_strcpy()`: copies a string

`_strcat()`: concatenates two strings

`_strdup()`: duplicates a string

`_strchr()`: searches a string for a character

`_strstr()`: searches for the first occurrence of a substring

`_strspn()`: gets the length of a prefix substring


## Compilation

`
gcc -Wall -Werror -Wextra -pedantic *.c -o hsh
`


### Testing code:
=============

```
$ ./hsh

($) ls

hsh main.c shell.c shell.h

$ exit
$
```
non-interactive mode:
```
$ echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
$
$ cat test_ls_2
/bin/ls
/bin/ls
$
$ cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
$
```

## Builtins
Our shell has support for the following built-in commands:

| Command             | Definition                                                                                |
| ------------------- | ----------------------------------------------------------------------------------------- |
| exit [n]            | Exit the shell, with an optional exit status, n.                                          |
| env                 | Print the environment.                                                                    |
| setenv [var][value] | Set an environment variable and value. If the variable exists, the value will be updated. |
| alias[name[='value]]| Reads aliases name                                                                        |
| unsetenv [var]      | Remove an environment variable.                                                           |
| cd [dir]            | Change the directory.                                                                     |
| help [built-in]     | Read documentation for a built-in.                                                        |

## Features
* Display a prompt and wait for the user to type a command. A command line always ends with a new line.
* If an executable cannot be found, print an error message and display the prompt again.
* Handle errors.
* Handling the “end of file” condition (Ctrl+D)
* Hanling the command line with arguments
* Handle the PATH
* Support the exit features and the exit status
* Handle the Ctrl-C to not terminate the shell
* Handling the command seperator `;`
* Handling `&&` and `||` logical operators
* Handle variable replacements `$?` and `$$`
* Handle the comments `#`
* Support the history feature
* Support the file input

## Creators 👨‍💻👩‍💻

1.

| Platform | Handle |
|----------|--------|
| `Github` | [Enzio Pelman](https://github.com/3nzio/) |
| `Twitter` | [Twitter](https://twitter.com/EnzioPelman) |

2.

| Platform | Handle |
|----------|--------|
| `Github` | [Memory-Verse](https://github.com/Memory-Verse/) |
| `Twitter` | [Twitter](https://twitter.com/LivingstoneTerk) |

## License

This project is licensed under the `MIT License` - see the `LICENSE` file for details.

## Acknowledgments :
- The creators of the C language.
- Alx-Africa .

