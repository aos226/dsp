# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > Command | Description
> > ------- | -----------
> > `pwd` | show current working directory path
> > `mkdir <directory>` | creating a directory
> > `rmd -rf <directory>`	| deleting a directory and all files in the directory with no prompting
> > `touch <filename>` | creating a file using `touch` command
> > `rm <file>`	| deleting a file
> > `mv <oldfilename> <newfilename>` | renaming a file
> > `ls -a` | listing hidden files
> > `cp <olddirectory/filename> <newdirectory/filename>` | copying a file from one directory to another
> > `mv <olddirectory/*.jpg> <newdirectory>` | move all jpeg files from one directory to another
> > `chmod <permissions> <path>	| change permissions of a file or directory
---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > Command | Description
> > ------- | -----------
> > `ls` | list files
> > `ls -a` | list hidden files
> > `ls -l` |  list file permissions
> > `ls -lh` | list file permissions with unit suffixes for the size of files
> > `ls -lah` | list permissions with unit suffixes for files and directory entries whose names begin with a dot
> > `ls -t` | list files sorted by time modified (most recently modified first)
> > `ls -Glp` | list file permissions with a slash after each filename that is a directory. In addition, colorized output is enabled.

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > Command | Description
> > ------- | -----------
> > `ls -1` | list files with each file on it's own line
> > `ls -d` | list only directories
> > `ls -r` | list files in reverse order
> > `ls -ltr` | list files in long form sorted by oldest file first
> > `ls -m` | list files as a comma separated list

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > xargs reads data from standard input and executes the command (supplied to it as an argument) based on the input read. The following example can be used to find specific files in the current directory:

> > `xargs find . -name`

> > If the user types in `*.txt` as the input, all of the text files will be displayed. 

