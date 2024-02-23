---
date: 2020-03-07
description: Userful Linux Shell Commands
categories:
  - Commands
---

# Linux Shell Script 

Below list most useful Linux Shell Script for reference.  
<!-- more -->

## Essential Toolkit 

### 1. alias

The alias command lets you give your own name to a command or sequence of commands. You can then type your short name, and the shell will execute the command or sequence of commands for you.

```
alias cls=clear
```

```
# create alias allow to find process ID (PID)
# then pipes them through grep command
alias pf="ps -e | grep $1"
```
### 2. cat

The cat command (short for “concatenate”) lists the contents of files to the terminal window.

```
cat .bash_logout
```

With files longer than the number of lines in your terminal window, the text will whip past too fast for you to read. You can pipe the output from cat through less to make the process more manageable.  With less you can scroll forward and backward through the file using the Up and Down Arrow keys, the PgUp and PgDn keys, and the Home and End keys. Type q to quit from less.

```
cat .bashrc | less
```

### 3. chmod

The chmod command sets the file permissions flags on a file or folder. The flags define who can read, write to or execute the file. 

```
#-owner|group|others
-rwxrwxrwx
```
**If the first character is a - the item is a file, if it is a d the item is a directory.** The rest of the string is three sets of three characters. From the left, the first three represent the file permissions of the **owner**, the middle three represent the file permissions of the **group** and the rightmost three characters represent the permissions for **others**. In each set, an r stands for read, a w stands for write, and an x stands for execute.

One way to use chmod is to provide the permissions you wish to give to the owner, group, and others as a 3 digit number.  The leftmost digit represents the owner. The middle digit represents the group. The rightmost digit represents the others. The digits you can use and what they represent are listed here:

```
0: No permission
1: Execute permission
2: Write permission
3: Write and execute permissions
4: Read permission
5: Read and execute permissions
6: Read and write permissions
7: Read, write and execute permissions

chmod -R 765 example.txt
```

### 4. chown 

The chown command allows you to change the owner and group owner of a file. You can use chown to change the owner or group, or both of a file. You must provide the name of the owner and the group, separated by a : character. You will need to use sudo. To retain dave as the owner of the file but to set mary as the group owner, use this command:

```
sudo chown dave:mary example.txt
```

### 5. curl

The curl command is a tool to retrieve information and files from Uniform Resource Locators (URLs) or internet addresses.

The curl command may not be provided as a standard part of your Linux distribution. Use apt-get to install this package onto your system if you’re using Ubuntu or another Debian-based distribution. On other Linux distributions, use your Linux distribution’s package management tool instead.

```
sudo apt-get install curl
```

This command retrieves the file for us. Note that you need to specify the name of the file to save it in, using the -o (output) option. If you do not do this, the contents of the file are scrolled rapidly in the terminal window but not saved to your computer.

```
curl https://raw.githubusercontent.com/torvalds/linux/master/kernel/events/core.c -o core.c
```

test web site request in container

```
curl https://google.com
```

### 6. df

The df command shows the size, used space, and available space on the mounted filesystems of your computer.

Two of the most useful options are the -h (human readable) and -x (exclude) options. The human-readable option displays the sizes in Mb or Gb instead of in bytes.

```
df -h -x squashfs
```

### 7. diff

The diff command compares two text files and shows the differences between them. There are many options to tailor the display to your requirements.

The -y (side by side) option shows the line differences side by side. The -w (width) option lets you specify the maximum line width to use to avoid wraparound lines. The two files are called alpha1.txt and alpha2.txt in this example. The --suppress-common-lines prevents diff from listing the matching lines, letting you focus on the lines which have differences.

```
diff -y -W 70 alpha1.txt alpha2.txt --suppress-common-lines
```

### 8. echo

The echo command prints (echoes) a string of text to the terminal window.

```
echo $USER
echo $HOME
echo $PATH
```

### 9. find

Use the find command to track down files that you know exist if you can’t remember where you put them.

```
find . -name *ones*
```
We do this using the -type option with the f parameter. The f parameter stands for files.

```
find . -type f -name *ones*
```

If you want the search to be case insensitive use the -iname (insensitive name) option.

```
find . -iname *wild*
```

### 10. finger

The finger command gives you a short dump of information about a user, including the time of the user’s last login, the user’s home directory, and the user account’s full name.

```
finger $USER
```

### 11. free

The free command gives you a summary of the memory usage with your computer. It does this for both the main Random Access Memory (RAM) and swap memory. The -h (human) option is used to provide human-friendly numbers and units. Without this option, the figures are presented in bytes.

```
free -h
```

### 12. grep

The grep utility searches for lines which contain a search pattern. When we looked at the alias command, we used grep to search through the output of another program, ps . The grep command can also search the contents of files. Here we’re searching for the word “train” in all text files in the current directory.

```
grep train *.txt
```

### 13. groups

The groups command tells you which groups a user is a member of.

```
groups mary
```

### 14. gzip

The gzip command compresses files. By default, it removes the original file and leaves you with the compressed version. To retain both the original and the compressed version, use the -k (keep) option.

```
gzip -k core.c
```

### 15. head

The head command gives you a listing of the first 10 lines of a file. If you want to see fewer or more lines, use the -n (number) option. In this example, we use head with its default of 10 lines. We then repeat the command asking for only five lines.

```
head -core.c
head -n 5 core.c
```

### 16. history

The history command lists the commands you have previously issued on the command line. You can repeat any of the commands from your history by typing an exclamation point ! and the number of the command from the history list.

```
history

# pick the number
!199
```


### 17. kill

The kill command allows you to terminate a process from the command line. You do this by providing the process ID (PID) of the process to kill. Don’t kill processes willy-nilly. You need to have a good reason to do so. In this example, we’ll pretend the shutter program has locked up.

```
# Find PID first
ps -e | grep shutter.

kill 1692
```

### 18. less

The less command allows you to view files without opening an editor. It’s faster to use, and there’s no chance of you inadvertently modifying the file. With less you can scroll forward and backward through the file using the Up and Down Arrow keys, the PgUp and PgDn keys and the Home and End keys. Press the Q key to quit from less.

```
less core.c
```

You can also pipe the output from other commands into less. To see the output from ls for a listing of your entire hard drive, use the following command:

```
ls -R / | less
```

### 19. ls 

more details check [man page](https://man7.org/linux/man-pages/man1/ls.1.html)

```
# use the -l (long) option
ls -l

# To use human-friendly file sizes include the -h (human) option
ls -lh

# To include hidden files use the -a (all files) option
ls -lha
```

### 20. man

The man command displays the “man pages” for a command in less . The man pages are the user manual for that command. Because man uses less to display the man pages, you can use the search capabilities of less.

For example, to see the man pages for chown, use the following command:

```
man chown
```

### 21. tree

 tree is a recursive directory listing program that produces a depth-indented listing of files.

 ```
 # If you are using Apple OS X, type:
 brew install tree

 # Display the tree hierarchy of a directory
 tree -a ./GFG

 ## list files with their permissions
 tree -p ./GFG 

 ```

### 22. mkdir

The mkdir command allows you to create new directories in the filesystem. 


```
mkdir invoces

mkdir -p quotes/yearly/2019
```

### 23. mv

The mv command allows you to move files and directories from directory to directory. It also allows you to rename files.

```
mv ~/Documents/Ukulele/Apache.pdf .

# rename file
mv Apache.pdf The_Shadows_Apache.pdf
```

### 24. passwd

The passwd command lets you change the password for a user. Just type passwd to change your own password.

```
sudo passwd mary
```

### 25. ping

The ping command lets you verify that you have network connectivity with another network device.

```
ping 192.168.4.18

# ping to run for a specific number of ping attempts, use the -c (count) option
ping -c 5 192.168.4.18

# To hear a ping use the -a(audible) option.
ping -a 192.168.4.18
```

### 26. ps

The ps command lists running processes. Using ps without any options causes it to list the processes running in the current shell.

```
ps

# to see all the processes related to a particular user
ps -u dave | less

# To see every process that is running, use the -e( every process)
ps -e | less

#  Shows User, All Processes and Terminal Information
ps aux
```

### 27. pwd

Nice and simple, the pwd command prints the working directory (the current directory) from the root / directory.

```
pwd
```

### 28. shutdown

The shutdown command lets you shut down or reboot your Linux system.

```
shutdown

# shut down immediately
shutdown now

```

### 29. SSH

Use the ssh command to make a connection to a remote Linux computer and log into your account.To make a connection, you must provide your user name and the IP address or domain name of the remote computer.

```
ssh mary@192.168.4.23
```

### 30. sudo

The sudo command is required when performing actions that require root or superuser permissions, such as changing the password for another user.

```
sudo passwd mary
```

### 31. tail

The tail command gives you a listing of the last 10 lines of a file. If you want to see fewer or more lines, use the -n (number) option.we use tail with its default of 10 lines. We then repeat the command asking for only five lines.

```
tail -n 5 core.c
```

### 32. tar

With the tar command, you can create an archive file (also called a tarball) that can contain many other files.
* -c (create) option
* -v (verbose) option
* -f (filename) option
* -z (gzip) option
* -j(bzip2) option
* -x (extract)

```
tar -cvf songs.tar Ukulele/

tar -cvzf songs.tar.gz Ukulele/

tar -cvjf songs.tar.bz2 Ukulele/

# extract files
tar -xvf songs.tar

tar -xvzf songs.tar.gz

tar -xvjf songs.tar.bz2
```

### 33. whoami or w

The w command lists the currently logged in users.

```
w
```

Use whoami to find out who you are logged in as or who is logged into an unmanned Linux terminal.

```
whoami
```

### 34. top

The top command shows you a real-time display of the data relating to your Linux machine. The top of the screen is a status summary. Detail check [here](https://www.geeksforgeeks.org/top-command-in-linux-with-examples/#:~:text=top%20command%20is%20used%20to,managed%20by%20the%20Linux%20Kernel.)

```
top
```

### 35. uname

You can obtain some system information regarding the Linux computer you’re working on with the uname command.

```
# See everything
uname -a 

# Use the -s (kernel name) option to see the type of kernel.
uname -s 

# Use the -r (kernel release) option to see the kernel release.
uname -r 

# Use the -v (kernel version) option to see the kernel version.
uname -v 

```

### 36. hostname

hostname used to either display or, with appropriate privileges, set the current host name of the system. The host name is used by many applications to identify the machine.

```
hostname -s 

```

### 37. du

The Linux “du” (Disk Usage) is a standard Unix/Linux command, used to check the information of disk usage of files and directories on a machine. 

```
# Using “-h” option with “du” command provides results in “Human Readable Format“
du -h /home/tecmint  

# To get the summary of a grand total disk usage size of an directory use the option “-s” as follows.
du -sh /home/tecmint 

# Using “-a” flag with “du” command displays the disk usage of all the files and directories.
du -a /home/tecmint 

```