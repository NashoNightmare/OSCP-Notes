# :shipit: OSCP - Notes
> Initialized on : 2021 / 01 / 30 

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/Intro.png)
### This is the online repository which I keep notes while studying the [OSCP(pirated) PWK 2.0]

## Contents
[![alt text](https://img.shields.io/badge/0.0-Git%20Commands-red)](https://github.com/NashoNightmare/OSCP-Notes#00-git-commands-cheatsheet-for-reference)

[![alt text](https://img.shields.io/badge/2.0-Linux%20in%20a%20nutshell-red)](https://github.com/NashoNightmare/OSCP-Notes#20-linux-in-a-nutshell-cheatsheet) [![alt text](https://img.shields.io/badge/Variables-Linux%20variable%20related%20commands-blueviolet)](https://github.com/NashoNightmare/OSCP-Notes#28-linux-variables)

[![alt text](https://img.shields.io/badge/3.0-Bash%20environment-red)](https://github.com/NashoNightmare/OSCP-Notes#30-bash-environment) [![alt text](https://img.shields.io/badge/Regex-Regex%20references-blueviolet)](https://github.com/NashoNightmare/OSCP-Notes#33-regex)

[![alt text](https://img.shields.io/badge/4.0-Practical%20Tools-red)](https://github.com/NashoNightmare/OSCP-Notes#40-practical-tools) [![alt text](https://img.shields.io/badge/Banners-Banner%20Grabbing-blueviolet)](https://github.com/NashoNightmare/OSCP-Notes#401-banners-aka-service-fingerprinting) [![alt text](https://img.shields.io/badge/OSI-OSI%20Model%20Quick%20ref-blueviolet)](https://github.com/NashoNightmare/OSCP-Notes#402-osi-layer-model)

[![alt text](https://img.shields.io/badge/5.0-Bash%20Scripting-red)](https://github.com/NashoNightmare/OSCP-Notes#50-bash-scripting)

[![alt text](https://img.shields.io/badge/6.0-Passive%20Information%20Gathering-red)](https://github.com/NashoNightmare/OSCP-Notes#60-passive-information-gathering)

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

> `host <url>` - Shows the corresponding IP address for a specific url. 

### 2.7 Other useful locations and files in linux
> `/etc/os-release` - OS Release information

>

### 2.8 Linux Variables
- Shell Variables (Variables which are only in scope of the shell)
	> `set` Command will show the all variables in the shell.
	
	> `set | grep <variable_name>` To see the specific variable

- Environment Variables (Variables which are available for system-wide)
	> `env` Command will show the all variables which are available system-wide.

	> `env | grep <variable_name>` Will return the specific variable name with its value.

- **Export** command
	
	We can use export command to export a variable to system-wide scope (Environment Variable) and also available for shell (Shell Variable). 

	Usage:

	![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/export2.png)

	**Good resource to understand export lot more way better** :

	![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/export0.png)
	
	![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/export1.png)

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

	> `[^/]` - Negated character class(In this given example it excludes '/' character.

	Only `]`  `\` `^` are metacharacters in a character class. To match these use backslash.

For more about character classes : [Character classes](http://www.regular-expressions.info/charclass.html)

Reference: [http://www.rexegg.com/](http://www.rexegg.com/)

Reference(NB:This resource is very good): [http://www.regular-expressions.info](http://www.regular-expressions.info)

Reference: [RexEgg Cheatsheet](http://www.rexegg.com/regex-quickstart.html#chars) 

### 3.4 Text-Fu - Tools
- **Grep** (Searches text files for the occurence given regex and outputs any line containing a match to stdout)
> `grep <regex>` - Use `-r` for recursive and `-i` for case ignorance.

> `grep -o <regex>` - Use `-o` for output the only matching text.

- **Sed** (Powerful text stream editor)
> `sed '' <file>` - Prints lines automatically

> `sed -n 'p' <file>` - Suppresses the automatic printing functionality and print manually

> `sed -n '1p' <file>` - Print first line only 

> `sed -n '1,5p' <file>` - Print the first 5 lines

> `sed 's/old-word/new-word/'` - Replace the old word with the new word (You can substitute the delimiter in front of the `s`)

> `sed 's/,$//'` - Replace the ending character only with a newline.

Reference : [Sed Tutorial](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)


- **Cut** (Used to extract a section from a line - But only support single character delimiter)
> `cut -f <field_number> -d "<delimiter used to seperate fields>"`

- **Awk** (Programming language designed for text processing)
> `awk -F "<delimiter>" '{print $<number of seperated item>}'`

> `awk -F "<delimiter>" '{print "Your_text" $<field1> "Your_text" $<field2>}'` - To add optional strings to the output

- **Tr** (Used to translate characters into another, Lot more like sed)
> `tr '<character_to_replace>` '<replace_with_this_character>'`

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

	> In the linux directory `/proc/` we could find out details about linux system kernel, processes and configuration parameters. It is not actually resides in hard drive that means that it exists only when the computer turned on and running which means exists in RAM.

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
		
		> `ps aux` - `-a`: All tty with other users, `-u`: Show user id, `-x`: Processes without controlling ttys

		> `pstree -aclp` : More detailed process display, Grab the process id from here and grep it from traditional `ps aux` for gather more details.
			

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

### 4.0.1 Banners (AKA Service Fingerprinting)
Banner refers to a text message received from the host, usually, it includes information about the open prots and services with their version numbers.
	
- Types of Banner Grabbing
	- Active Banner Grabbing
	- Passive Banner Grabbing

- Banner Grabbing Tools
	> `whatweb`, `cURL`, `wget`, `telnet`, `Nikto`, `Nmap`, `Dmitry`, `BurpSuite`, `Netcraft`, `ID Serve`, `Wappalyzer(Browser Extension)`, `HTTP Header Live(Browser Extension)`

### 4.0.2 OSI Layer Model

**Developer Concentration Section**

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

**Network Engineer Concentration Section**

Layer 4 - **Transport** (End to End Connections) (Datagrams or Segments)
	
	- Message segmentation (Splits message to smaller units)
	- Handles transportation issues between host.
	- Ensures data transport reliability.
	- Establishes, maintains and terminates virtual circuits.
	- Flow control (Manage data transmission).
	- Session Multiplexing.
		
	
	- TCP (Transmission Control Protocol)
		- If packet missing it will be re transmitted.		
		- Uses 3-way handshake.

	- UDP (User Datagram Protocol)
		- Does not provide reliability.
		- If packet are dropped they are lost.
		- Lightweight

Layer 3 - **Network** (Data Delivery) (Packets)
	
	- Have routing capabilities. Selects best path to deliver data.
		- OSPF (Open Shortest Path First)
		- BGP (Border Gateway Protocol)
		- IS-IS (Intermediate System-to-Intermediate System).
	
Layer 2 - **Data Link** (Physical Addressing and Access to Media) (Frames)
	
	- Defines how data is formatted for transmission and how access to the network is controlled.
	- Error Detection.

Layer 1 - **Physical** (Binary Transmission)(Bits)
	
	- What state represents 0 or 1.
	- Defines electrical, mechanical, procedural and functional specifications for activating maintaining
and deactivating the physical link.
	- Focused with physical devices and physical cabling.
	- Medium,


**More Details for OSI Layer Model**

- Process of conversion from layer to layer. (Always communication happens between layer n to layer n of the other side. Eg: Layer 7 communicates with Layer 7)
- [NetworkChuck Demonstrates the process of OSI Model well](https://www.youtube.com/watch?v=3kfO61Mensg&list=PLIhvC56v63IJVXv0GJcl9vO5Z6znCVb1P&index=5) 

### 4.1 NetCat

Utility that reads and writes data across network connections, using TCP or UDP protocols.

- Client mode 
	- Check if a port is open or closed.
	- Read a banner from the service listening on a port.
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

### 4.6 TCP Dump


## 5.0 Bash Scripting

**Shebang** : `#!/bin/bash`, `#!/bin/bash -x` : `-x` flag for additional debug output -  This is what makes this a “Bash script” as opposed to another type of shell script, like a “C Shell script”.

**Initializing Variables** : `variable_name="Variable_Content"` 

**Referring Variables** : `echo "Your variable is $variable_name"` , `echo $variable_name` , `variable_name2="Variable 1 $variable_name"`

**Command substituition(Assign the output of a program to a variable)** : `variable_name=$(command)`

**Arguments** : `echo "The first two arguments are $1 and $2"`- The first 9 arguments to the Bash script can be $1 to $9.
![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/special_bash_variables.png)

**Reading User Input** : `read variable_name` , To refer the user input `echo "The user input is $variable_name"`

**Conditional Statements** :
	
	If [<some_test>]
	then
		<perform_an_action>
	elif [<some_test>]
	then
		<perform_different_action>
	else
		<perform_yet_another_different_action>
	fi

![alt txt](https://github.com/NashoNightmare/OSCP-Notes/blob/master/common_test_command_operators.png)

**Boolean Logic Operators**
1. Using Boolean Operators in non-conditional statements : 
	
	- `command1 && command2` - Command 2 executes if command 1 succeeds(Exit Status 0).
	- `command1 || command2` - Command 2 executes if command 1 fails(Any exit Status except 0).

2. Using Boolean Operators in conditional statements : The same functionality of Boolean operators on C program conditional statements occurs herea as well.

**Loops**
1. For loop

		_______________________________________
		for <var_name> in <list>
		do 
			<action_to_perform>
		done
		_______________________________________
		for <var_name> in $(seq 1 10)
		do
			<action_to_perform>
		done
		_______________________________________
		for <var_name> in {1..10}
		do 
			<action_to_perform>
		done
		_______________________________________

2. While loop			

		_______________________________________
		counter=1
		while [	$counter -lt 10 ]
		do
			<action_to_perform>
		done
		_______________________________________
		while [ $counter -le 10 ]
		do
			<action_to_perform>
		done
		_______________________________________
		while [ $counter -gt 10 ]
		do
			<action_to_perform>
		done
		_______________________________________
		while [ $counter -ge 10 ]
		do
			<action_to_perform>
		done
		_______________________________________

**Functions**

		_______________________________________
		function_name(){
		<commands>
		}
		_______________________________________
To use the function : `function_name

We can pass the arguments to the function by using same procedure we done for the bash programs. Literally the function in a bash program is a program-in-a-program

Example : 

		function function_one {
			echo "Hello $1"
		}

		function_one 20

To declare local variables : Use `local` keyword to define a local variable.
		
		_______________________________________
		function_name(){
			local_variable = "content"
		}
		_______________________________________


## 6.0 Passive Information Gathering.
We could stage out the five phases of hacking as defined in the image below. The first step of the phases is Passive Information Gathereing. AKA OSINT (Open Source Intelligence). And we should maintain high level of secrecy about our actions and intentions.

Passive Information Gathering is the process of collecting openly available information about the target, Generally without any direct interaction with the target.

**The five phases of hacking**
![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/five-phases.png)

### 6.1 Taking Notes
Most important thing to do in a passive recon is taking notes in well detailed format, despite the fact the information seems advantageous or disadvantageous.

### 6.2 Website Recon
If the client has a website, we can gather basic information by simply browsing the website. Website may contain subdomains it is lot more convenient if we have a eye on those subdomains for more information. And we can look on the employee or company related person's social media information. 

Special note by Nasho : We could possibly enhance our OSINT skill by taking random ctf challenges and wargames.

### 6.3 WhoIs Enumeration
Database tool that can provide information about a domain name, such as the name server and registrar. This information is often public since registrars charge a fee for provate registration.

> `whois <domain_name>`

### 6.4 Google Hacking
> `site:<example.com>` - Shows only the results from the address. Also shows subdomains and pages.

> `site:<example.com> filetype:<file_type>` - Shows the results only corresponding to the file type and website.

> `site:<example.com> -filetype:<file_type>` - Shows the results only corresponding to the website while excluding corresponding filetype.

> `intitle:"<title>" "words"` - To find pages that contain "title" in the title and the words "words". Most useful instance is word "parent directory".

The GHDB (Google Hacking Databse) contains multitudes of creative searches that demonstrate the power of creative searching with combined operators.

Link (GHDB) :- [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)

### 6.4 Netcraft
Offers site reports.
Link : [https://searchdns.netcraft.com/](https://searchdns.netcraft.com/)

### 6.5 Recon-ng
Recon-ng is a module based framework for web-based information gathering. Recon-ng displays the results of a module to the terminal but it also stores them in databse.

`recon-ng`

Creating Workspace - Very useful when inheriting different module results.

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/recon-ng0.png)

Searching and installing modules

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/recon-ng1.png)

Loading and executing modules

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/recon-ng2.png)

To view stored data

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/recon-ng3.png)

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/recon-ng4.png)

### 6.6 Open Source Code
Looking up for the openly available source codes in specific companies. 

- GitHub
- GitLab
- SourceForge

### 6.7 Shodan
Is a search engine that crawls devices connected to internet including but not limited to the World Wide Web. This includes the servers that run websites but also devices like routers and IoT devices.

Link : [www.shodan.io](https://www.shodan.io/)

### 6.8 Security Header Scanner
There are several other specialty websites that we can use to gather information about a website or domain’s security posture. Some of these sites blur the line between passive and active information gathering, but the key point for our purposes is that a third-party is initiating any scans or checks.

Link : [https://securityheaders.com/](https://securityheaders.com/)

### 6.9 SSL Server Test
This tool analyzes a server’s SSL/TLS configuration and compares it against current best practices.

Link : [https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)

### 6.10 Pastebin
A pastebin or text storage site is a type of online content hosting service where users can store plain text, e.g. to source code snippets for code review.

Link : [https://pastebin.com/](https://pastebin.com/)

### 6.11 Email Harvesting
Gathers emails, names, subdomains, IPs, and URLs from multiple public data sources.

> `theHarvester -d <domain> -b google` - `-d`:Domain, `-b`:Data source to search

### 6.12 Social Searcher

Link : [https://www.social-searcher.com/](https://www.social-searcher.com/)

### 6.13 Use Forums
We can use forums and developer bases like Quora, StackOverFlow, Dev.to to tackle down employees by Social engineering them.

### 6.14 Information Gathering Frameworks
- OSINT Framework - Online available well-ordered OSINT tools and resources collection.
	Link : [https://osintframework.com/](https://osintframework.com/)
- Maltego - Combination of searching tools and strategies.
	Available with kali linux and freely available community edition that needs registration.

### 6.15 WiGLE (Wireless Geogrphic Logging Engine)
WiGLE is a website for collecting information abou the different wireless hotspots around the world. Users can register on the website and upload hotspot data like GPS coordinates, SSID, MAC(BSSID) and the encryption type used on the hotspots discovered.

Link : [https://wigle.net/](https://wigle.net/)

### 6.15 Wayback Machine
The Wayback Machine is a digital archive of the World Wide Web, founded by the Internet Archive, a nonprofit library based in San Francisco. It allows the user to go “back in time” and see what websites looked like in the past.

Link: [https://archive.org/web/](https://archive.org/web/)
