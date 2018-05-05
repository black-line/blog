title: Command Lline 学习笔记
date: 2015-11-25 10:42:51
tags: [Command Line, notes]
---
`touch [filename]` - create a new file
`pwd` - print working directory
`cd` - change directory

<!--more-->

___
###### ls
`-a` - lists all contents, including hidden files and directories

`-l` - lists all contents of a directory in long format
```
$ ls -l
drwxr-xr-x 5  cc  eng  4096 Jun 24 16:51  action
drwxr-xr-x 4  cc  eng  4096 Jun 24 16:51  comedy
drwxr-xr-x 6  cc  eng  4096 Jun 24 16:51  drama
-rw-r--r-- 1  cc  eng     0 Jun 24 16:51  genres.txt
```
1.==Access rights==. These are actions that are permitted on a file or directory.
2.==Number of hard links==. This number counts the number of child directories and files. This number includes the parent directory link (..) and current directory link (.).
3.==The username of the file's owner==. Here the username is cc.
4.==The name of the group that owns the file==. Here the group name is eng.
5.The ==size== of the file in bytes.
6.The ==date & time== that the file was ==last modified==.
7.The ==name== of the file or directory.

`-t` - order files and directories by the time they were last modified.
`-alt` - multiple options are used together
___
### cp
1. `-[filename1] [filename2]` - copy the contents of filename1 into filename2.
2. `-[filename1] [filename2] [path]` - a new copy of filename1 and filename1 in [path] directory.
3. `-*` - copy all files
4. `-m*.txt` - copy all files starting with "m" and ending with "txt"
___
### mv
1. `-[filename1] [filename2]` - rename a file
___
### rm
1. The rm command deletes files and directories.
2. The `-r` is an option that modifies the behavior of the rm command. The -r stands for "recursive," and it's used to delete a directory and all of its child directories.
3. Be careful when you use `rm`! It deletes files and directories permanently.
___
### cat > >> <
1. `echo "Hello" > hello.txt` - The `>` command redirects the standard output to a file.
2. `cat hello.txt` - The `cat` command outputs the contents of a file to the terminal.
3. `cat oceans.txt > continents.txt` - `>` takes the standard output of the command on the left, and redirects it to the file on the right. Note that - - `>` overwrites all original content in **continents.txt**.
4. `cat glaciers.txt >> rivers.txt` - `>>` takes the standard output of the command on the left and appends (adds) it to the file on the right.
5. `cat < lakes.txt` - `<` takes the standard input from the file on the right and inputs it into the program on the left.
6. `cat volcanoes.txt | wc` - `|` is a "pipe". The `|` takes the standard output of the command on the left, and pipes it as standard input to the command on the right.
7. `wc` - `wc` command outputs the number of lines, words, and characters in volcanoes.txt, respectively.
8.  `sort lakes.txt` - `sort` takes the standard input and orders it alphabetically for the standard output.
9. `uniq` - filter out adjacent, duplicate lines in a file.
___
### grep
- `grep Mount mountains.txt` - `grep` stands for "global regular expression print". It searches files for lines that match a pattern and returns the results.
1. `grep -i` - be case insensitive.
2. `grep -R` - searches all files in a directory and outputs filenames and lines containing matched results. -R stands for "recursive"
3. `grep -Rl` - searches all files in a directory and outputs only filenames with matched results. -R stands for "recursive" and l stands for "files with matches".
___
### sed
- `sed 's/snow/rain/[g]' forests.txt` - `sed` stands for "". It accepts standard input and modifies it based on an expression, before displaying it as output data. It is similar to "find and replace".
1. `s` -  stands for "substitution". it is always used when using sed for substitution.
2. `snow` -  the search string, the text to find.
3. `rain` -  the replacement string, the text to add in place.
the above command will only replace **the first instance** of "snow" on a line.
4. `g` - means "global"
***
# Enviroment
***
**~/.bash_profile** is the name of file used to store environment settings. It is commonly called the "bash profile". When a session starts, it will load the contents of the bash profile before executing commands.
- The `~` represents the user's home directory.
- The `.` indicates a hidden file.
- The name **~/.bash_profile** is important, since this is how the command line recognizes the bash profile.
1. The command `nano ~/.bash_profile` opens up **~/.bash_profile** in nano.
2. The text `echo "Welcome, Jane Doe"` creates a greeting in the bash profile, which is saved. It tells the command line to `echo` the string "Welcome, Jane Doe" when a terminal session begins.
3. The command `source ~/.bash_profile` activates the changes in **~/.bash_profile** for the current session. Instead of closing the terminal and needing to start a new session, `source` makes the changes available right away in the session we are in.