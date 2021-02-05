# :shipit: OSCP - Notes
> Initialized on : 2021 / 01 / 30 

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/Intro.png)
### This is the online repository which I keep notes while studying the [OSCP(pirated) PWK 2.0]

## Contents
[![alt text](https://img.shields.io/badge/0.0-Git%20Commands-red)](https://github.com/NashoNightmare/OSCP-Notes#00-git-commands-cheatsheet-for-reference)

[![alt text](https://img.shields.io/badge/2.0-Linux%20in%20a%20nutshell-red)](https://github.com/NashoNightmare/OSCP-Notes#20-linux-in-a-nutshell-cheatsheet)

[![alt text](https://img.shields.io/badge/3.0-Bash%20environment-red)](https://github.com/NashoNightmare/OSCP-Notes#30-bash-environment)[![alt text](https://img.shields.io/badge/Regex-Regex%20references-blueviolet)](https://github.com/NashoNightmare/OSCP-Notes#33-regex)

## 0.0 Git commands cheatsheet for reference.
> `git add .` - Stage all changed files, ready for commit.

> `git commit` - Commit all staged files to versioned history.

> `git push` - Push local changes to the origin.

> `![alter text](http:\\url-to-the-image\image)` - To add an image to a specific location in a file.

> `git config credential.helper store` -> `git push` -> Add the credentials - To avoid loging everytime push the local to origin. 

## 2.0 Linux in a nutshell cheatsheet.

### 2.1 Linux Filesystem Hierarchy 
![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/file_hierarchy_linux.png)
### 2.2 Man pages
> $ man ls

Man pages contain not only information about user commands, but also documentation regarding system administration commands, programming interfaces, and more.

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/sections-man.png)

> `man -k passwd` - To perform a keyword search.

> `apropos partition` - Another way to perform a keyword search through the man pages.

### 2.3 Locating files 
> `locate <file_name or directory>` - Quickest way to find files.

> `which <file_name or directory>` - Returns pathnames of files or links which would execute in current environment. (By PATH variable)

> `find / -name <file>` 

> `find / -name <file> -type d` - Directory search

> `find / -name <file> -type f` - File search

### 2.4 Linux Services
Start/Stop a Service
> `$ sudo systemctl start/stop/enable/disable <service_name>` or `$ sudo service <service_name> start/stop`

Check if a service is running
> `$ netstat -tunap | grep <service_name>` or `$ ss -antlp | grep <service_name>`

To see available service table
> `$ systemctl list-unit-files`

Notes:
Service names for SSH:`ssh` , HTTP:`apache2`
Default index.html location: `/var/www/html`

### 2.5 Extracting archives 
> `tar xvfz <file>` - Extract tar file

> `gunzip <file>` - Extract gz file

### 2.6 Other useful commands
> `cat <file> | wc -l` - Returns line count of a specific file 

> `head <file>` - Returns first 10 lines in a file

> `cat <file> | sort -u` - Show unique lines

> `cat <file> | uniq -c` - Show the count of unique lines

> `cat <file> | sort -urn` - Sort out unique lines in reverse order according to the numeric value

> `uname -a` - Linux version

> 

### 2.7 Other useful locations and files in linux
> `/etc/os-release` - OS Release information

>

## 3.0 Bash Environment
When opening a new terminal window, a new Bash process, which has its own **Environment variables**, is initialized. One of the most commonly-referenced environment variable is **PATH (Colon seperated directory paths that bash will search through whenever a command is run without a full path.** 

To view the contents of a environment variable :
> `$ echo $PATH` - To view the contents of a given environment variable.

Some other useful environment variables : `USER` , `PWD` , `HOME` , `$`-Process id of the current shell

> `$ export <name>=<value>` - To define a environment variable. NB: *If we do not use `export` to define the variable the variable will be limited to the current shell.

> `$ env` - To view all environment variables

### 3.3 RegEx
A pattern which describes a certain amount of text.

- **Metacharacters** [Those characters should used with escape characters when it is used as a literal.]
	> `\` `^` `$` `.` `|` `?` `*` `+` `(` `)` `[` `]` `{` `}`

	All other characters(non-meta) should not escaped with backslash. Because it may create regex token with specific meaning.
	> `'` `"` - Not metacharacters

	To use regex in programming language string such as C:\temp
	> Regex : `C:\\\\temp`

- **Non printable character tokens**
	> `\t`-Tab, `\r`-Return, `\n`-NewLine, `\a`-Bell, `\e`-Escape, `\f`-FormFeed, `\r\n`-WindowsTextNewLine, `\R`-LineBreak(UnicodeIncluded)

- **Character classes**
	> `[ ]` - To define a character class (Matches only for one character by default, Use quantifier for more options)

	> `[^]` - Negated character class

	Only `]`  `\` `^` are metacharacters in a character class. To match these use backslash.

For more about character classes : [Character classes](http://www.regular-expressions.info/charclass.html)

Reference: [http://www.rexegg.com/](http://www.rexegg.com/)

Reference(NB:This resource is very good): [http://www.regular-expressions.info](http://www.regular-expressions.info)

Reference: [RexEgg Cheatsheet](http://www.rexegg.com/regex-quickstart.html#chars) 

### 3.4 Text-Fu - Tools
- **Grep** (Searches text files for the occurence given regex and outputs any line containing a match to stdout)
> `grep <regex>` - Use `-r` for recursive and `-i` for case ignorance.

- **Sed** (Powerful text stream editor)
> `sed '' <file>` - Prints lines automatically

> `sed -n 'p' <file>` - Suppresses the automatic printing functionality and print manually

> `sed -n '1p' <file>` - Print first line only 

> `sed -n '1,5p' <file>` - Print the first 5 lines

> `sed 's/old-word/new-word/' - Replace the old word with the new word (You can substitute the delimiter in front of the `s`)

Reference : [Sed Tutorial](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)


- **Cut** (Used to extract a section from a line - But only support single character delimiter)
> `cut -f <field_number> -d "<delimiter used to seperate fields>"`

- **Awk** (Programming language designed for text processing)
> `awk -F "<delimiter>" '{print $<number of seperated item>}'`

> `awk -F "<delimiter>" '{print "Your_text" $<field1> "Your_text" $<field2>}'` - To add optional strings to the output

### 3.5 Diffing

> `comm file1 file2` - Outputs 3 columns (1-lines unique to file1, 2-lines unique to file2, 3-lines common in both files

> `diff -c file1 file2` - Another tool to find the differences in two files.

> `vimdiff file1 file2` - More visual aided tool.

>

### Managing Processes
- **Processes**

	> The kernel maintain information about each process to help keep things organized, and each process is assigned a number called **Process ID (PID)**

	> Foreground Processes(interactive processes) - These are initialized and controlled though a terminal session. There has to be a user connected to the system to start such processes. They haven't started automatically as a part of system functions/services.

	> Background Processes(automatic processes) - are processes not connected to a terminal. They don't expect any user input.

	> Daemons - These are special types of background processes that start at system startup and keep ruinning forever as a service. They don't die. Started as a system tasks. They can controlled by a user via the init process.



For more indepth [linux processes](https://github.com/NashoNightmare/Linux-Kernel#linux-process-creation).

- **Jobs**

	> The linux shell also introduces the concept of **Jobs** to ease the user's workflow during the terminal session. A combination of processes (Such a composite command) is considered as a job in linux.

	- **Background Processes(`bg`)**

		> `<command> &` - append '&' to run the command in background.
		
		> We could suspend a job by `Ctrl + Z`. Resume it in the background by using the `bg` command.

	- **Foreground Processes(`fg` and `jobs`)**	

		> `jobs` - Returns the jobs that are running in the current shell.

		> `fg` - To bring back last stopped job to foreground. or `fg %<process_number>` to bring back specified process to the foreground(Stopped or background running).


