# This is a note for linux courese
# Create at 2018.05.14
<hr>

# Lecture 1:
## Linux Distribution
* Redhat
    * Banks
    * Airlines
    * ....
* Ubuntu
    * startups
    * Saas
    * Social networks..
* Linux Distro = kernel + software
*

# lecture 2:
## Common Directories
* /   "Root", the top of the file system hierarchy
* /bin  Binaries and other executable programs
* /etc  System congfiguration files
* /home Home Directories
* /opt  Optional or third party software
* /tmp  Temporary space, typically cleared on reboot
* /usr  User related programs
* /var  Variable data, most notably log files.
* path:
![path_linux](path_linux.png)
![path2_linux](path2_linux.png)

## Comprehensive Directory Listing:
* /boot
* /cdrom
...

## superuser / root:
![superuser](superuser.png)
* root = admin
* ~ :
    * ~root = /Root
    * ~dorothy = /home/dorothy
    * ~ftp = /srv/ftp

## Basic Linuc Commands:
* ls  => Lists directory contents
* cd  => Changes the current Directory
* pwd  => Displays the present working Directory
* cat  => Concatenates and displays (content) files
* echo  => Displays arguments to the screen
* man  => Displays the online manual
* exit  => Exits the shell or your current session.
* clear  => Clears the screen .


* ls -l :more details about the file
### environment variable:
* PATH:
    * ./command = Execute command in this dir
* OLDPWD:
### location of the full path:
* which

## Directories:
* .  => This Directory
* ..  => The parent directory
* cd -  change to the previous directory

## Creating and Removing Directories:
* mkdir [-p] directory => Create a directory
* rmdir [-p] director => Remove a directory
    * Only remove empty directory
* rm -rf directory => Recursively removes directory

## ls:
* ls -l  : show the long format
* ls -a : show the hidden files
* ls -a -l / ls -l -a / ls -al / ls -la is all the same.
* Use ls -F to reveal file types:
    * / directory
    * @ link
    * * Executable
* ls -t  : list files sorted by time
* ls -r  : reverse order
* ls -latr : long listing including all files reverse sorted by time
* ls -R  : Lists files recursively
* ls -d  : only show the directory name
* ls --color  : Colorize the output
## tree:

# Lecture 3:
## File and Directory Permission
* - : Regular file
* d : Directory
* l : Symbolic link
* r : Read
* w : Write
* x : Execute
## Permission Categories:
* u : User
* g : Group
* o : Other
* a : all

### Groups:
* Every user is in at least one group
* User can belong to many groups
* Groups are used to organize users.
* The groups command display a user's groups
    * eg: group root
* You can also use **id -Gn**.
![secret_Decoder_Ring](secret_decoder_ring.png)

### Changing Permission:
* chmod  : Change mode command
* ugoa  : User category; user, group, other, all
* +-=  : Add, subtract, or set permissions
* rwx  : Read, Write, Execute
* eg:
```
chmod g+w sales.data
ls -l sales.data

chmod u+rwx,g-x sales.data

chmod a=r sales.data
```

* Numeric Based Permission:
![numeric_permission](numeric_permission.png)
* Order Has Meaning:
![commonly_used_permission](commonly_used_permission.png)
* eg:
```
chmod 400 my-cat
```
* We should avoid 777 or 666 for some security concern

### Working with Groups
* New files belong to your primary group
* The _chgrp_ command changes the group.


### Directory Permissions Revisited
* **Permissions on a directory can effect the files in the directory**.
* If the file permissions look correct, start checking directory permissions.
* Work your way up to the root.

### File Creation Mask:
* File creation mask determines default permissions.
* If no mask were used permissions would be:
    * 777 for directories
    * 666 for files
* The umask Command:
    * umask [-S] [mode]
    * Sets the file creation mask to mode, if give
    * Use **-S to for symbolic notation**
    * how to use:
        ![umask](umask.png)
    * common umask modes:
        * 022
        * 002
        * 077
        * 007
    * 8 umask permutations:
    ![umask_2](umask_2.png)
    * Special Modes:
        * umask 0022 is the same as umask 022
        * chmod 0644 is the same as chmod 644
        * The special modes are :
            * setuid
            * setgid
            * sticky
        * **touch** either create a file if not exist, or update the timestamp of the file

## Displaying the Content of File:
* displaying content:
    ![display](assets/markdown-img-paste-20181211191905570.png)

* head: first 10 lines
* tail: last 10 lines
* tail -1 file.txt: only last line
* tail -f file.txt: view as the file grows, eg log file.

## Nano Editor:
easiler than vi..

## Vi Editor:
* cheat sheet:
![](assets/markdown-img-paste-20181211200406643.png)
* turn on line numbering:
   ```
    :set nu
   ```
* turn off line numbering:
    ```
    :set nonu

    ```
* Repeating command: <number><command>:
    * 5k: move up a line 5 times
    * 80i<Text><ESC> = Insert <Text> 80 times
    * 80i_<ESC> = Insert 90 "_" characters.

* Deleting Text:
    * x Delete a character
    * dw Delete a word
    * dd Delete a line
    * D Delete from the current position.

* Changing Text:
    * r Replace the current character
    * cw Change the current word.
    * cc Change the current line
    * c$ CHange the text from the current position.
    * C Same as C$
    * ~ Reverses the case of a character

* Copying and Pasting
    * yy Yank(copy) the current line
    * y<position> Yank the <position>
    * p Paste the most recent deleted or yanked text.

* Undo and Redo:
    * u Undo
    * Ctrl-R Redo


* Searching:
    * /<pattern> Start a forward searching
    * ?<pattern> Start a reverse searching


## Emacs Editor
*

## Find File:
* find [path..] [expression]
    * Options:
        * -name pattern  Find files and directories that match pattern.
        * -iname pattern  Like -name, but ignore case.
        * -ls  Performs an ls on each of the found items. (eg: find / README.md -ls)
        * -mtime days  Find files that are days old.
        * -size num  FInds file that are of size num.
        * -newer file  Find files that are newer than  file.
        * -exec command {}\;   Run command against all the files that are found. (eg: find . -exec file {} \;)

## sort
* sort file
    * Options
        * -k F  Sort by key. F is the field number (eg, sort -u -k2 filename)
        * -r  Sort in reverse order
        * -u  Sort unique.

## Creating a collection of Files
* tar [-] c|x|t f tarfile [pattern]  Create, extract or list contents of a tar archive using pattern, if supplied.
    * Options
        * c  Create a tar archive
        * x  Extract files from the archive
        * t  Display the table of contents(list)
        * v  Be verbose
        * z  Use compression
        * f file   Use this file

## Compressing Files to Save Space
* gzip  Compress files.
* gunzip  Uncompress files
* gzcat  Concatenates compressed files
* zcat  Concatenates compressed files.

## Disk Usage
* du  Estimates file usage
* du -k  Display sizes in Kilobytes
* du -h  Display sizes in human readable format.


## Wildcards
* "*"  matches zero or more characters
* ?   matches exactly one character*
* []  A character class. (eg, ca[nt]?)
* [!]  Matches any of the characters NOT included between the brackets. Matches exactly one character. (eg, [!aeiou])
* Use two characters separated by a hyphen to create a range in a character class.(eg, [a-g])
* Named Character Classes
    * [[:alpha:]] matches alphabetic letters. (Both lower and upper cases)
    * [[:alnum:]] matches alphanumeric letters. (Any upper or lower  and digit)
    * [[:digit:]]
    * [[:lower:]]
    * [[:space:]] white space.
    * [[:upper:]]

* Matching Wildcard patterns
    * \  escpae character. Use if you want to match a wildcard character.
        * match all files that end with a question mark:
            * "*\?"

## Redirection
* >  Redirects standard output to a file. Overwrites (truncating) existing contents.
* >>  Redirects standard output to a file. Appends to any existing contents.
* <  Redirects input from a file to a command.
* &  Used with redirection to signal that a file descriptor is being used.
* 2>&1  Combine stderr and standard output.
* 2>file  Redirect standard error to a file.
* >/dev/null  Redirect output to nowhere


## Comparing the contents of Files
* diff file1 file2  Compare two files.
* sdiff file1 file2  Side-by-side comparison.
* vimdiff file1 file2  Highlight differences in vim.
    * output: eg. 3c3; where the first "3" is the line number of first file, and so as the second "3".
    * LineNumFile1 - Action - LineNumFile2
        * Action = (A)dd(C)hange(D)elete
    * in vimdiff:
        * ctrl-w w   Go to the next window
        * :q    Quit current window
        * :qa   Quit all

## Searching in FIles and Using Pipes
* grep  Display lines matching a pattern
    * grep pattern file
        * Options
            * -i  Perform a search, ignoring case.
            * -c  Count the number of occurrences in a file
            * -n  Precede output with line numbers.
            * -v  Invert Match. Print lines that don't match.

* file  file_name  Display the file type.

* strings  Display printable strings
* |    Pipe symbool
    * command-output  |  command-input
    * eg.  cat file | grep patter

* cut [file]   Cut out selected portions of file. If file is omitted, use standard input.
    * Options
        * -d delimiter  Use delimiter as the field separator
        * -f N  Display the Nth field.
        * eg. cut -d' ' -f2,5
* tr  Translate character. (eg, tr ":" " "  translate ":" to " "
* column -t   Show in table format


## Copying FIles over the Network
* SCP - Secure copy
* SFTP - SSH file transfer protocol

* scp source destination   Copy source to destination
* sftp host      Start a secure file transfer session with host.
* ftp           Start a file transfer session with host.

## Environment Variables
* printenv
    * printenv HOME
    * printenv home
* echo $HOME
    * echo $home

### Creating Environment Variables
* export VAR="value"
    * export EDITOR="vi"
    * do not inclue space around "="
    * export TZ="US/Pacific"
### Removing Environment Variables
* unset VAR
    * unset TZ
### Persisting Environment Variables
* cat ~/.bash_profile
* export TZ="US/Central"


## Processes and job control
* ps Display process status
    * -e  Everything, all processes
    * -f  Full format listing
    * -u username  Display username's processes
    * -p pid  Display information for PID

    * -ef  Display all processes, full
    * -eH  Display a process tree.
    * -e --forest  DIsplay a process tree
    * -u username  DIsplay user's processes.
* pstree  Display processes in a tree format
* top     Interactive process viewer
* htop    Interactive process viewer.

# Background and Foreground Processes
* command &    STart command in background
* Ctrl-c       Kill the foreground process
* Ctrl-z       Suspend the foreground process.

* bg [%num]    Background a suspended process
* fg [%num]    Forground a background process
* kill         Kill a process by job number or PID
* jobs [%num]  List jobs.
    * jobs %%   Current job
    * jobs %+   Current job
    * jobs %-   Previous job

# Killing Processes
* Ctrl-c
* kill [-sig] pid    Send a signal to a process
* kill -l            Display a list of signals

* eg kill signal is 9. So: kill -9 123

# Crontab
* A time based job scheduling service.
## Crontab Format
crontab Format![](assets/markdown-img-paste-20190125171239898.png)
* examples:
crontab example 1![](assets/markdown-img-paste-20190125171709166.png)

crontab example 2![](assets/markdown-img-paste-20190125173004395.png)

* Redirecting output:
redirecting![](assets/markdown-img-paste-20190125172903256.png)

* shortcuts
crontabShortcuts![](assets/markdown-img-paste-20190125214332947.png)

* run crontab:
    * vim my-cron
        * 0 7 * * 1 /weekly-report
    * crontab file_name

* list cron jobs:
    * crontab -l
* edit cron jobs:
    * crontab -e
* remove all of your cron jobs
    * crontab -r

# Switching Users and Running Commands as Others
* su [username]  Change user ID or become superuser
* options:
    * -           A hyphen is used to provide an environment similar to what the user would expect had the user logged in directly.
    * -c command  Specify a command to be executed.
* whoami
* Sudo
    * option:
        * sudo Option![](assets/markdown-img-paste-20190125231924407.png)
        * sudo with su![](assets/markdown-img-paste-20190125232141977.png)

# Shell History and Tab Completion
* Shell history is stored in memory and on disk.
    * ~/.bash_history
    * ~/.history
    * ~/.histfile
* history   Displays the shell history
* HISTSIZE  Controls the number of commands to retain in history (usually up to 500)
    * export HISTSIZE=1000     customize the HISTSIZE
* ! Syntax
    * !N      Repeat command line number N
    * !!      Repeat the previous command line
    * !string   Repeat the most recengt command starting with "string"
    * !:N <Event> <Separator> <Word>
        * !        Repeat a command line (or event).
            * ! = The most recent command line.
            * ! = !!
        * :N      Represents a word on the command line.
            * 0 = command, 1 = first argument, etc
    * !^      Represents the first argument.
        * !^  = !:1
    * !$     Represents the last argument
    * eg: head files.txt sorted_files.txt notes.txt
        * !^ = files.txt
        * !$ = notes.txt
## Searching Shell history
* Ctrl-r   Reverse shell history search
* Enter    Execute the command
* Arrows   Change the command
* Ctrl-g   Cancel the search


# Install Softwares  (Package Manager)
## RPM Distros (Linux)
### yum:
* yum search string             Search for string
* yum info [package]            Display info
* yum install [-y] package      Install package
* yum remove package            Remove package

### rpm
* rpm -ql package             List package's files
* rpm -ivh package.rpm        Install package
* rpm -e package              Erase (uninstall) package

## DEB Distros (Debian)
### APT - Advanced Packaging Tool
* apt-cache search string        Search for string.
* apt-get install [-y] package   Install package.  (-y, automatically answer "yes")
* apt-get remove package         Remove package, leaving configuration.
* apt-get purge package          Remove package, deleting configuration
* apt-cache show package         Display information about package.

### dpkg
* dpkg -l                     List installed packages
* dpkg -S /path/to/file       List file's package.
* dpkg -L package             List all files in package.
* dpkg -i package.deb         install package
