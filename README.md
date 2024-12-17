# bash-scripting

Bash stands for Bourne Again Shell. It has been around for a very long time and
works with Linux, Windows Subsystem for Linux, and even the Mac terminal. It's
lightweight and good for simple scripts. It does not offer Object Oriented
Programming like Python or Java. Also difficult syntax compared to Python.

Ansible is an open-source automation tool worth looking into if you need to
manage multiple large-scale IT systems. But you can use Bash in tandem with
Python and Ansible. Knowing the basics could make a big difference in certain
situations.

Vim is a good simple text editor for Linux. More complex text editors would be
VS code, Gooey, or Sublime.

## VIM basics

Create a text file with:

```sh
vim textfile.txt
```

<li>Press "i" to insert some text.</li>
<li>Start with something like "Hello World". </li>
<li>Press escape to leave insert mode. </li>
<li>Enter ":w" to save what you entered. </li>
<li>Press ":q" to exit the file.</li>
<li>Press ":q!" to exit without saving the file.</li>

To print whatever is in the file, type:

```sh
cat textfile.txt
```

For a sh file, use the bash command to print its output:

```sh
bash shelltest.sh
```

Open up the file again (vim shelltest.sh) and provide the shebang (#!). This
tells the shell script which interpreter to use. Follow up the #! with the full
path to the intrepreter:

#!/bin/bash echo Hello World!

Ask the ls command to give the long format:

```sh
ls -l
```

Next we need to give the file permission to be executed:

```sh
chmod u+x shelltest.sh
```

You can now run this file with:

```sh
./shelltest.sh
```

## Variables

FIRST_NAME=Mark 
LAST_NAME=Buckle 
echo $FIRST_NAME $LAST_NAME

echo What is your first name?
read FIRST_NAME
echo What is your last name?
read LAST_NAME

echo Hello $FIRST_NAME $LAST_NAME

## Positional Arguments

Arguments that are at a specific position, counting from one (0) onwards. Position 0 is reserved for the shell itself.

echo Hello $1 $2

## Output / Input Redirection 

### Piping

Piping allows you to perform a specific action on the output of a command. Let's say the output of a command is very long and you want to filter something out. Piping allows you to filter out what you want. "|" is the pipe symbol.

Examples:
```sh
echo Hello there | grep there

ls -l /usr/bin | grep bash 
```
### Output redirection

Symbols used:
> symbol to write to a file
>> symbol to append to a file

Example:
To print Hello World! into a file called hello.txt:
```sh
echo Hello World! > hello.txt
```
Note that if you use the > symbol again, it will overwrite the previous output with the new output rather than adding on to it. 
This is where appending comes in place:
```sh
echo Good day to you >> hello.txt
```

To get a word count:
```sh
wc -w hello.txt
```
However it shows the name of the file. To hide the file name:
```sh
wc -w < hello.txt
```

To write what you want to place in your output:
```sh
cat << EOF
```
Make sure to finish/close your statement with EOF

To feed a string into a command. Make sure the string is in double quotes:
```sh
wc -w <<< "Hello there word count"
```

## Test Operators

"$?" returns the value of the exit code on the last executed command. Exit code "0" means the command was executed without any issues. Exit code "1" means the values were not the same.


## Video tutorial:

https://www.youtube.com/watch?v=tK9Oc6AEnR4
