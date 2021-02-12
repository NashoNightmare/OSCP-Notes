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

> `find / -mtime +n` - Finds the files and directories modified more than n days ago.

> `find / -mtime -n` - Finds the files and directories modified less than n days ago. (Use `-mmin [+,-]n` for Minutes instead of days. 

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

### 3.6 Managing Processes
- **Processes**

	> The kernel maintain information about each process to help keep things organized, and each process is assigned a number called **Process ID (PID)**

	> Foreground Processes(interactive processes) - These are initialized and controlled though a terminal session. There has to be a user connected to the system to start such processes. They haven't started automatically as a part of system functions/services.

	> Background Processes(automatic processes) - are processes not connected to a terminal. They don't expect any user input.

	> Daemons - These are special types of background processes that start at system startup and keep ruinning forever as a service. They don't die. Started as a system tasks. They can controlled by a user via the init process.



For more indepth [linux processes](https://github.com/NashoNightmare/Linux-Kernel#linux-process-creation).

- **Jobs**

	> The linux shell also introduces the concept of **Jobs** to ease the user's workflow during the terminal session. A combination of processes (Such a composite command) is considered as a job in linux.

	- **Background Jobs (`bg`)**

		> `<command> &` - append '&' to run the command in background.
		
		> We could suspend a job by `Ctrl + Z`. Resume it in the background by using the `bg %<job_number>` command.

	- **Foreground Jobs (`fg` and `jobs`)**	

		> `jobs` - Returns the jobs that are running in the current shell.

		> `fg` - To bring back last stopped job to foreground. or `fg %<job_number>` to bring back specified process to the foreground(Stopped or background running).

- **Process Control**
	
	- **PS Command(The swiss army knife of Process Management)**

		> `ps -ef` - To see every processes system now runs. (`-e` - Every process , `-f` - Display full format)

		> `ps -fC <command_name>` - Select by command.

		> `kill <PID>` - Kill the process by process ID.

### 3.7 File and Command Monitoring

Please refer to [Section 2.6](https://github.com/NashoNightmare/OSCP-Notes#26-other-useful-commands) to more commands.

- **Tail**
	
	> `tail -f <file_name>` - Live monitoring of a file that updates continuously.
	
	> `tail -n<number_of_lines> <file_name>` - Last desired number of lines of a file.

- **Watch**
	
	> `watch -n <interval_time_in_sec> "<command>"` - Runs a command after specified interval and updates the terminal.

### 3.8 Downloading Files

- **Wget**

	> `wget -O <specified_name_to_be_saved> <url_for_the_file>` - Downloads files using HTTP/HTTPS/FTP protocol.

- **Curl**

	Used to transfer data to or from a server using a host of protocols including IMAP/S, POP3/S, SCP, SFTP, SMB/S, SMTP/S, TELNET,TFTP, and others. Can use this to download or upload files and build complex requests.

	For man pages : [Curl](https://curl.se/docs/manpage.html)

	> `curl -o <save_as> <url_to_the_file>` - Equivalent to the wget command.

	> You can specify multiple URLs or parts of URLs by writing part sets within braces and quoting the URL as in: `http://site.{one,two,three}.com`

	> You can get sequences of alphanumeric series by using [] as in : `ftp://ftp.example.com/file[1-100].txt`, `ftp://ftp.example.com/file[a-z].txt`, `ftp://ftp.example.com/file[001-100].txt`(Leading zeros)

	> `curl -X <request> <url>` - Make requests for specified url.

- **Axel**

	Download accelerator that transfers a file from a FTP or HTTP server through multiple connections. This tool has a vast array of features, but the most common is -n, which is used to specify the number of multiple connections to use. 

	> `axel -a -n 20 -o <save_as> <url_to_the_file>` - `-a` for more concise progress indicator, `-n` for number of multiple connections to use. 

## 4.0 Practical Tools

### Extra tutorials - Helps reading this chapter.

#### Banners (AKA Service Fingerprinting)
Banner refers to a text message received from the host, usually, it includes information about the open prots and services with their version numbers.
	
- Types of Banner Grabbing
	- Active Banner Grabbing
	- Passive Banner Grabbing

- Banner Grabbing Tools
	> `whatweb`, `cURL`, `wget`, `telnet`, `Nikto`, `Nmap`, `Dmitry`, `BurpSuite`, `Netcraft`, `ID Serve`, `Wappalyzer(Browser Extension)`, `HTTP Header Live(Browser Extension)`

#### OSI Layer Model
- Developer Concentration Section
Layer 7 - **Application**(FTP, Telnet, HTTP, SSH, IMAP, POP3, SMTP)
	- Provides access for users.
	- Provides network services to application processes.
	- Identify communication partners.
	- Provides user authentication.

Layer 6 - **Presentation** (Data Representation/ Syntax)
	- Ensures that data is readable by receiving system.
	- Formats data to be presented to application layer.
	- Structures data.
	- Negotiates data transfer syntax for application layer (ASCII or UNICODE).
	- Provides encryption.

Layer 5 - **Session** (Interhost communication)
	- Establishment maintenance and termination of sessions between applications.
	- Maintains security / name recognition / logging.
	- Two application processes on different machines can establish a session.
	Example: 
		- NetBIOS (Network Basic Inpt/Output System)
		- PPTP (Point to point tunneling protocol)

- Network Engineer Concentration Section
Layer 4 - **Transport** (End to End Connections)
	-
	

### 4.1 NetCat

Utility that reads and writes data across network connections, using TCP or UDP protocols.

- Client mode 
	- Check if a port is open or closed.
	- Read a [banner](https://github.com/NashoNightmare/OSCP-Notes#banners-aka-service-fingerprinting) from the service listening on a port.
	- Connect to a network service manually.
	
	> `nc -nv <ip_address> <port>` - `-n`:Skip DNS name resolution, `-v`:Add some verbosity.

- Server mode
	> `nc -lvnp <port>` - `-l`:Listen, `-v`:Verbose output, `-n`:Skip DNS name resolution, `-p`:Define listening port.

- **Applications of NetCat**
	- Blind Shell

### 4.2 SoCat

### 4.3 PowerShell

### 4.4 PowerCat

### 4.5 Wireshark (Traffic  Sniffer)

Wireshark uses Libpcap101 (on Linux) or Winpcap102 (on Windows) libraries in order to capture packets from the network.		


