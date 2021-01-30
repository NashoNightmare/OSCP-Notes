# :shipit: OSCP - Notes
> Initialized on : 2021 / 01 / 30 

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/Intro.png)
### This is the online repository which I keep notes while studying the [OSCP(pirated) PWK 2.0]

## **0.0 Git commands cheatsheet for reference.**
> `git add .` - Stage all changed files, ready for commit.

> `git commit` - Commit all staged files to versioned history.

> `git push` - Push local changes to the origin.

> `![alter text](http:\\url-to-the-image\image)` - To add an image to a specific location in a file.

> `git config credential.helper store` -> `git push` -> Add the credentials - To avoid loging everytime push the local to origin. 

## **2.0 Linux in a nutshell cheatsheet. **

### 2.1 Linux Filesystem Hierarchy 
![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/file_hierarchy_linux.png)
### 2.2 Man pages
> $ man ls

Man pages contain not only information about user commands, but also documentation regarding system administration commands, programming interfaces, and more.

![alt text](https://github.com/NashoNightmare/OSCP-Notes/blob/master/sections-man.png)

To perform a keyword search.
> man -k passwd

Another way to perform keyword searches through the man pages.
> apropos partition 

### 2.3 Locating files 
> `locate <file_name or directory>` - Quickest way to find files.

> `which <file_name or directory>` - Returns pathnames of files or links which would execute in current environment. (By PATH variable)

> `find / -name <file>` 

> `find / -name <file> -type d` - Directory search

> `find / -name <file> -type f` - File search

### 2.4 Linux Services
