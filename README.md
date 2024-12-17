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

## Video tutorial:

https://www.youtube.com/watch?v=tK9Oc6AEnR4
