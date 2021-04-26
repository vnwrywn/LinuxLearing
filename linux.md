# Table of Contents

- [Table of Contents](#table-of-contents)
- [Command Line](#command-line)
  - [Command Line and Shell](#command-line-and-shell)
  - [Shell Command Structure](#shell-command-structure)
  - [Basic Shell Commands](#basic-shell-commands)
  - [Manual Pages](#manual-pages)
    - [Manual Structure](#manual-structure)
    - [How to read the synopsis](#how-to-read-the-synopsis)
  - [Vi Text Editor](#vi-text-editor)
  - [Wildcards](#wildcards)
    - [Basic set of wildcards](#basic-set-of-wildcards)
    - [Example](#example)
  - [Permissions](#permissions)
    - [Types of permissions](#types-of-permissions)
    - [Permissions subjects](#permissions-subjects)
- [Bash Scripting](#bash-scripting)
  - [Variables](#variables)
    - [Special variables](#special-variables)
  - [Input](#input)
  - [Operations](#operations)
    - [let](#let)
    - [expr](#expr)
    - [Double parentheses](#double-parentheses)
    - [Length of a variable](#length-of-a-variable)
  - [Conditionals](#conditionals)
    - [If statements](#if-statements)
    - [Case Statements](#case-statements)
    - [Test](#test)
    - [Boolean Operations](#boolean-operations)
  - [Loops](#loops)
    - [While loops](#while-loops)
    - [Until loops](#until-loops)
    - [For loops](#for-loops)
    - [Break and continue](#break-and-continue)
    - [Select](#select)
  - [Funtions](#funtions)
    - [Local variable](#local-variable)
    - [Overriding commands](#overriding-commands)

# Command Line

Command line is an interface that allows user to enter commands by typing its respective command. The
command line gives feedback outputs in the form of text. The reason for using the command line is that
the command line are more suitable for some taks than the GUI, such as data manipulation and file management.

## Command Line and Shell

Shell is an environment in which we can run our commands, programs, and shell scripts. Whereas the
command line is the program we use to type in the commands we want to run in shell. In a nutshell,
A shell is a language in which we give the commands, and command line is the tool we use to send out these
commands. There are various shell available, and bash (bourne again shell) is the most commonly used.

## Shell Command Structure

- A shell command have a particular way in which they have to be written in.
- A shell command is case sensitive. command and Command is seen as different commands.
- Shell command structure: command [options] [arguements]
- Although, not all commands requires either options or arguements.

An arguement is the operand of a command. Just like operands to functions, some commands may be able to recieve multiple arguements. The structure of such command is as such: command [arguements] [arguements] [arguements]

An option is a modifier for a command which changes the way it is executed.
A dash(-) usually preceeds an option, and some commands may allow several options in one command. Some
options for some commands may have a short form (preceeded by a dash) and a long form (preceeded by
two dashes).
In short form, some option may be typed in this form.
command -[option][option][option]
In long form, multiple options have to be typed in this manner.
command --[option] --[option] --[option]

## Basic Shell Commands

1. cd
   Used to change directory.
   cd [-L|-P] [DIRECTORY] -> used to change the current directory to the given input
   Shortcuts:
   ~ -> shortcut to home directory
   . -> shortcut to current directory
   .. -> shortcut to upper directory
2. pwd [OPTION] -> Used to print the current working directory
3. ls [OPTION]... [file]... -> used to list the content of current directory
   -l -> used to give detailed information of the content of current directory
   -a -> used to list the contents of a directory, including hidden files
4. mkdir [OPTION]... DIRECTORY... -> Used to create a directory in the current directory
5. rmdir [OPTION]... DIRECTORY... -> Used to remove a directory in the current directory
6. touch [OPTION]... FILE... -> Used to create a blank file
7. cp [OPTION]... SOURCE... DIRECTORY -> used to copy a file or directory to the destination
8. rm [OPTION]... [FILE]... -> used to remove a file
9. cat [OPTION]... [FILE]... -> Used to concatenate files.
   cat [filename1] [filename2] -> used to show the contents from both of the file with the given
   filenames
   cat >[filename] -> used to create a file with the given 
   cat [filename1] > [filename2] -> used to copy the content from [filename1] to [filename2]
   cat [filename1] >> [filename2] -> used to append the contents of one file to the end of another file.
   tac [filename] -> used to display content in reverse order.

## Manual Pages

man [command name] -> used to look up the manual pages for a particular command

man -k [keyword] -> search the manual pages containing the given keyword

### Manual Structure

1. User commands
2. System calls
3. C library functions
4. Devices and special files
5. File formats and conventions
6. Games
7. Miscellaneous
8. System administration

A manual page of a command may consists of: name, synopsis, description, options, exit status, examples,
see also, environment, bugs, authors, history, and copyright.

### How to read the synopsis

- [] -> optional
- <> -> mandatory
- [  |  ] -> choose one
- ... -> allows multiple input

## Vi Text Editor

vi [−rR] [−c command] [−t tagstring] [−w size] [file...]
A command line text editor designed to overcome the limitations of the command line. Vi has two modes
of operations: command mode, which cause action to be taken on the file, and Insert mode in which
entered text is inserted into the file.
In the command mode, every character typed is a command that does something to the text file being edited;
a character typed in the command mode may even cause the vi editor to enter the insert mode. In the
insert mode, every character typed is added to the text in the file; pressing the <Esc> (Escape) key
turns off the Insert mode.

## Wildcards

Wildcards, also referred as globbing, are a set of building blocks that allow you to create a
pattern defining a set of files or directories.

### Basic set of wildcards

- \* -> represents zero or more characters
- ? -> represents a single character
- [] -> represents a range of characters (including)
- [\^] -> represents a range of characters (excluding)

### Example
```
cat *.txt
grep a=?
```

## Permissions

Dictates whether or not you are allowed to read, write, and execute a file.
The permissions for a file can be viewed by doing a long listing. It is structured as below.
-rwxrwxrwx
0123456789
0 -> identifies the file type; - for a normal file, d for a directory
1-3 -> represents the permissions for the owner
4-6 -> represents the permissions for the group
7-9 -> represents the permissions for other
Changing the permissions of a file can be done using the following command:
chmod [permissions] [path]

### Types of permissions

- r (read) -> allows the viewing of the contents of the file
- w (write) -> allows the changing of the contents of the file
- x (execute) -> allows the executing or running of the file (if it is a program or script)

### Permissions subjects

- owner - the singular owner of the file (usually also is the creator of the file)
- group - a single group to whom the file belongs
- others - everyone else who is not in the group or the owner


# Bash Scripting

Bash scripting is making a series of commands in a plain text file called bash scripts. The goal of
bash scripting is to make everyday routine less tedious to perform.

## Variables

A variable is a temporary store for a piece of information. There are two operation that can be performed
on a variable; setting and reading the value of a variable. A variable is read and reffered by placing a
"$" sign before the name of the variable. A variable may be placed in anywhere in a script, in which it
will be replace by its value when the script is run.

### Special variables

- $0 -> The name of the Bash script.
- $1 - $9 -> The first 9 arguments to the Bash script. (As mentioned above.)
- $# -> How many arguments were passed to the Bash script.
- $@ -> All the arguments supplied to the Bash script.
- \$? -> The exit status of the most recently run process.
- \$$ -> The process ID of the current script.
- $USER -> The username of the user running the script.
- $HOSTNAME -> The hostname of the machine the script is running on.
- $SECONDS -> The number of seconds since the script was started.
- $RANDOM -> Returns a different random number each time is it referred to.
- $LINENO -> Returns the current line number in the Bash script.

## Input

Most scripts will require inputs to perform their designated tasks. These inputs will then be assigned as
a value of a variable or used right away. The following command will assign the input to a variable
named var.
```
read var
```

## Operations

An arithmetic operations is often an integral part of our daily routine.

### let

Allows simple arithmetic operations.

let <"arithmetic expression">

- \+ -> performs additions
- \- -> performs substractions
- \\* -> performs multiplications
- / -> performs divisions
- ++ -> performs increment
- -- -> performs decrement
- % -> returns modulus

e.g:
```
let "var = 1 + 1"
echo $var # 2
let var++
echo $var # 3
```

### expr

Similiar to let, but prints the result instead of assigning it to a variable

expr item1 operator item2

e.g:
```
expr 1 + 1 # 2
var=$( expr 2 + 2 )
echo $var # 4
```

### Double parentheses

Similiar to let.

$(( expression ))

e.g:
```
var=$(( 1 + 1 ))
echo var # 2
(( var++ ))
echo var # 3
```

### Length of a variable

Used to get the number of characters a variable has.

${#variable}

e.g:
```
var=11
echo ${#var} # 2
```

## Conditionals

### If statements

Functions like any other if function

```
if [ <some test> ]
then
    <commands>
[elif [ <some test> ]
then
    <different commands>]
[else
    <other commands>]
fi
```

### Case Statements

Again, not much difference from the usual case statements

```
case <variable> in
<pattern 1>)
    <commands>
    ;;
<pattern 2>)
    <other commands>
    ;;
esac
```

### Test

The following are operators for test:
- ! EXPRESSION -> The EXPRESSION is false.
- -n STRING -> The length of STRING is greater than zero.
- -z STRING -> The lengh of STRING is zero (ie it is empty).
- STRING1 = STRING2 -> STRING1 is equal to STRING2
- STRING1 != STRING2 -> STRING1 is not equal to STRING2
- INTEGER1 -eq INTEGER2 -> INTEGER1 is numerically equal to INTEGER2
- INTEGER1 -gt INTEGER2 -> INTEGER1 is numerically greater than INTEGER2
- INTEGER1 -lt INTEGER2 -> INTEGER1 is numerically less than INTEGER2
- -d FILE -> FILE exists and is a directory.
- -e FILE -> FILE exists.
- -r FILE -> FILE exists and the read permission is granted.
- -s FILE -> FILE exists and it's size is greater than zero (ie. it is not empty).
- -w FILE -> FILE exists and the write permission is granted.
- -x FILE -> FILE exists and the execute permission is granted.
- *= will do a string comparison, but -eq will do a numarical comparison*

### Boolean Operations

- && -> and
- || -> or

## Loops

### While loops

Regular while loops. You know the drill.

```
while [ <some test> ]
do
   <commands>
done
```

### Until loops

Like while loops, but the commands will be executed until the test becomes true

```
until [ <some test> ]
do
   <commands>
done
```

### For loops

I'm starting to feel that i don't need to add an explaination for every single thing.

```
for var in <list>
do
   <commands>
done
```

Or

```
for value in {<int1>..<int2>}
do
   echo $value
done
```

### Break and continue

Yup, like any other break and continue

- break -> stops the looping process
- continue -> stops the current cycle and skips ahead to the next

### Select

Allows you to make a simple menu system

```
select var in <list>
do
    <commands>
done
```

## Funtions

```
function_name () {
   <commands>
   [return]
}
```

OR

```
function function_name {
   <commands>
   [return]
}
```

### Local variable

Used to make a variable only available for a function

```
local var_name=<var_value>
```

### Overriding commands

Overrides a command by creating a method of the same name as the command
e.g:

```
ls () {
    command ls -lh
    }
ls # ls -lh
```
![That's All folks](https://i.imgur.com/pFoXaqU.jpg)