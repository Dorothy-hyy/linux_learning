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

## 








diaplay
