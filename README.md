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

Exampel:
```sh
[hello = hello]
echo $?
```
or
```sh
[1 = 1]
echo $?
```
## If / Elif / Else

"${1,,}" is some argument converted to lower case. 

```sh
#!/bin/bash
if [ ${1,,} = mark ]; then
        echo "Oh, you're the boss here. Welcome!"
elif [ ${1,,} = help]; then
        echo "Just enter your username, duh!"
else
        echo "I don't know who you are. But you're not the boss of me!"vim ifelifelse.sh
fi
```

## Case Statements

Easier to read and better than if/elif/else when checking for multiple values.

If the option matches the case, then we will perform the action bound to that option.

Note that "|" is not a pipe symbol in this case, just a separator for options.

```sh
#!/bin/bash
case ${1,,} in
        mark | administrator)
                echo "Hello, you're the boss here!"
                ;;
        help)
                echo "Just enter your username!"
                ;;
        *)
                echo "Hello. You're not the boss of me."
fi
```

## Arrays

Create an array:
```sh
MY_FIRST_LIST=(one two three four five)
```

To print out the full array:
```sh
echo ${MY_FIRST_LIST[@]}
```

To print out a specific index (in this case the first item [0]):
```sh
echo ${MY_FIRST_LIST[0]}
```

## For Loops

Create an array:
```sh
MY_FIRST_LIST=(one two three four five)
```
Write a simple for loop:
```sh
for item in ${MY_FIRST_LIST[@]}; do echo -n $item | wc -c; done
```

## Functions

```sh
#!/bin/bash

showuptime(){
        up=$(uptime -p | cut -c4-)
        since=$(uptime -s)
        cat << EOF
-----
THis machine has been up for ${up}
It has been running since ${since}
-----
EOF
}
showuptime
```

When you define variables, they are available to the entire script by default. To avoid overwriting global variables you need to use local variables.

```sh
#!/bin/bash

showuptime(){
        local up=$(uptime -p | cut -c4-)
        local since=$(uptime -s)
        cat << EOF
-----
THis machine has been up for ${up}
It has been running since ${since}
-----
EOF
}
showuptime
```

### Post arguements

```sh
#!/bin/bash

showname(){
        echo hello $1
}
showname Mark
```

## AWK

Allows you to filter file contents or the output of a command in such a way that we can print out the most essential parts and get the output the way we like it.

### AWK Example 1
Create a simple testfile:
```sh
echo one two three > testfile.txt
vim testfile.txt
```

Print the first word in the testfile with AWK:
```sh
awk '{print $1}' testfile.txt
```
### AWK Example 2
Create a simple csv file and enter "one,two,three". Make sure to include commas instead of spaces:
```sh
vim csvtest.csv
```
Print the first word in the csv file with AWK:
```sh
awk -F, '{print $1}' csvtest.csv
```

### AWK Example 3
Print out a word within a statement:
```sh
echo "Just get this word: Hello" | awk '{print $5}'
```

## SED 

When you want to change/modify values within files, SED is a great option. 
```sh
vim sedtest.txt
```

Change the value of a specific word within the file:
```sh
sed 's/oldword/newword/g' sedtest.txt
```
's' stands for substitute and is in the mode place.
'g' stands for globally and is in the location place.

Let's say we want to keep the original file in a backup file:
```sh
sed -i.ORIGINAL 's/oldword/newword/g' sedtest.txt
```
To view the original:
```sh
vim sedtest.txt.ORIGINAL
```
## Video tutorial:

https://www.youtube.com/watch?v=tK9Oc6AEnR4
