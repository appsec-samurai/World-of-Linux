# *****Linux-Commands*****

### Table of Contents

---

| No. | Topic                                                                   |
| --- | ----------------------------------------------------------------------- |
| 1   | [**System information**](#system-information)				            |
| 2   | [**Hardware information**](#hardware-information)			            |
| 3   |	[**User information**](#user-information)                               |
| 4   | [**File and directory commands**](#file-and-directory-commands)         |
| 5   | [**File permissions**](#file-permissions)                               |
| 6   | [**Networking**](#networking)                                           |
| 7   | [**Installing packages**](#installing-packages)                         |
| 8   | [**Disk usage**](#disk-usage)                                           |
| 9   | [**Search Files**](#search-files)                                       |
| 10  | [**SSH**](#ssh)                                                         |
| 11  | [**Vi/Vim-commands**](#vi/vim-commands)                                 |

### System information

1.  **Print all information**: `uname` is mainly used to print system information.

```bash
$ uname -a
```

2.  **Print Architecture**:

```bash
$ uname -m
```

3.  **Print network hostname**:

```bash
$ uname -n
```

4.  **Print Operating System**:

```bash
$ uname -o
```

5.  **Print kernel release**:

```bash
$ uname -r
```

6.  **Print kernel name**:

```bash
$ uname -s
```

**[⬆ Back to Top](#table-of-contents)**

### Hardware information

1.  **Print information about your `Linux system hardware` run this command.**

```bash
$ sudo lshw
```

2.  **Print `summary of your hardware information` by using the `-short` option.**

```bash
$ sudo lshw -short
```

3.  **Generate output as an `html file`, you can use the option `-html`.**

```bash
$ sudo lshw -html > lshw.html
```

4.  **View `Linux CPU` Information.**

```bash
$ lscpu
```

5.  **Collect `Linux Block Device` Information.**

```bash
$ lsblk
```

6.  **View `all block devices` on your system then include the `-a` option.**

```bash
$ lsblk -a
```

7.  **Print `USB Controllers` Information.**

```bash
$ lsusb
```

8.  **Print `PCI Devices` Information.**

```bash
$ lspci
```

9.  **Produce output in a `tree format`.**

```bash
$ lspci -t
```

10.  **Produce detailed information about each `connected device`.**

```bash
$ lspci -v
```

11.  **Print `SCSI Devices` Information.**

```bash
$ sudo apt-get install lsscsi        [on Debian derivatives]
# yum install lsscsi                 [On RedHat based systems]
# dnf install lsscsi                 [On Fedora 21+ Onwards]

After installation, run the `lsscsi` command:
$ lsscsi
```

12.  **Show device sizes.**

```bash
$ lsscsi -s
```

13.  **Print Information about `SATA Devices`.**

```bash
$ sudo hdparm /dev/sda1
```

14.  **Print information about device geometry in terms of cylinders, heads, sectors, size, and the starting offset of the device, use the -g option.**

```bash
$ sudo hdparm -g /dev/sda1
```

15.  **Check `Linux File System` Information.**

```bash
$ sudo fdisk -l
```

16.  **Check `Linux Hardware Components` Information.**

```bash
You can also use the dmidecode utility to extract hardware information by reading data from the DMI tables.
To print information about memory, run this command as a superuser.
```
```bash
$ sudo sudo dmidecode -t memory
$ sudo dmidecode -t system
$ sudo dmidecode -t bios
$ sudo dmidecode -t processor
```

**[⬆ Back to Top](#table-of-contents)**

### User Information

1. **who** It is used to get information about currently logged in user on to system. If you don't provide any option or arguments, the command displays the following information for each logged-in user.

1. Login name of the user
2. User terminal
3. Date & Time of login
4. Remote host name of the user

```bash
$ who
appsec-samurai :0           2023-01-16 04:58 (:0)
appsec-samurai pts/0        2023-01-16 04:59 (:0)
```

2. **whoami:** It display the system’s username

```bash
$ whoami
appsec-samurai
```

3. **id:** It display the user identification(the real and effective user and group IDs) information

```bash
$ id
uid=1000(appsec-samurai) gid=1000(appsec-samurai) groups=1000(appsec-samurai) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

4. **groups:** This command is used to display all the groups for which the user belongs to.

```bash
$ groups
appsec-samurai
```

5. **finger:**  Used to check the information of any currently logged in users. i.e, It displays users login time, tty (name), idle time, home directory, shell name etc.

```bash
$ finger
Login          Name            Tty      Idle  Login Time   Office     Office Phone   Host
appsec-samurai appsec-samurai *:0             Jan 16 04:58                           (:0)
appsec-samurai appsec-samurai  pts/0          Jan 16 04:59                           (:0)
```

This may not be available by default in many linux machines. In this case, you need to install it manually.

```bash
$ sudo yum install finger
$ sudo apt install finger
```

6. **users:** Displays usernames of all users currently logged on the system.

```bash
$ users
appsec-samurai appsec-samurai
```

7. **adduser :** Create a new user in the system.

```bash
$ adduser "username"

```

7. **grep:** It  is a powerful pattern searching tool to find information about a specific user from the system accounts file: /etc/passwd.

```bash
$ grep -i appsec-samurai /etc/passwd
appsec-samurai:x:1000:1000:appsec-samurai:/home/appsec-samurai:/bin/bash
```

8. **w Command:** It(W) is a command-line utility that displays information about currently logged in users and what each user is doing.

```bash
w [OPTIONS] [USER]

Example:
$ w
  02:36:50 up  4:32,  2 users,  load average: 0.08, 0.67, 0.69
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
appsec-s :0       :0               Mon04   ?xdm?   3:36   0.35s /usr/libexec/gnome-session-binary --session gnome-classic
appsec-s pts/0    :0               Mon04    2.00s  0.17s 14.08s /usr/libexec/gnome-terminal-server 
```

9. **last or lastb:** Displays a list of last logged in users on the system. You can pass user names to display their login and hostname details.

```bash
last [options] [username...] [tty...]

Example:
$ last
appsec-s pts/0        :0               Mon Jan 16 04:59   still logged in   
appsec-s :0           :0               Mon Jan 16 04:58   still logged in   
reboot   system boot  3.10.0-1127.el7. Mon Jan 16 04:57 - 02:39  (21:41)    
reboot   system boot  3.10.0-1127.el7. Mon Nov 28 23:15 - 02:39 (49+03:24)  
appsec-s pts/0        :0               Mon Nov 28 23:11 - 23:14  (00:03)    
appsec-s :0           :0               Mon Nov 28 21:14 - crash  (02:00)    
reboot   system boot  3.10.0-1127.el7. Mon Nov 28 21:14 - 02:39 (49+05:25)  

wtmp begins Mon Nov 28 21:14:00 2022
```

10. **lastlog:** The `lastlog` command is used to find the details of a recent login of all users or of a given user.

```cmd
$ lastlog
Username         Port     From             Latest
root             pts/0                     Tue Jan 17 02:39:16 -0800 2023
bin                                        **Never logged in**
daemon                                     **Never logged in**
adm                                        **Never logged in**
lp                                         **Never logged in**
sync                                       **Never logged in**
shutdown                                   **Never logged in**
sshd                                       **Never logged in**
avahi                                      **Never logged in**
postfix                                    **Never logged in**
tcpdump                                    **Never logged in**
appsec-samurai   pts/0                     Tue Jan 17 02:39:29 -0800 2023
```

**[⬆ Back to Top](#table-of-contents)**

### File and directory commands

1. **pwd** The pwd(Present Working Directory) command is used to print the name of the present/current working directory starting from the root.
   ```bash
   $ pwd
   /home/appsec-samurai
   ```

2. **ls**: The `ls` command is used to list files or directories. It also accepts some flags or options that changes how files or directories are listed in your terminal.

    ```bash
     Syntax:
     ls [flags] [directory]

     Example:
     $ ls
     Desktop  Documents  Downloads  Music  Pictures  Public  snap  Templates  Videos  

     //Listing files & directories with time in a rever order
     $ ls -ltr
     drwx------ 3 appsec-samurai appsec-samurai 4096 Oct 20 20:15 snap
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Desktop
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Videos
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Templates
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Public
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Pictures
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Music
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Downloads
     drwxr-xr-x 2 appsec-samurai appsec-samurai 4096 Oct 20 20:15 Documents


     //Home directory
     $ ls ~
     Desktop    Downloads  Pictures  Sudheer    test   test.txt
     Documents  Music      Public    Templates  test1  Videos
    ```

    Below are the list of possible options for `ls` command,

    ```cmd
    -a Show all (including hidden)
    -R Recursive list
    -r Reverse order
    -t Sort by last modified
    -S Sort by file size
    -l Long listing format
    -1 One file per line
    -m Comma-­sep­arated output
    -Q Quoted output
    ```

3. **mkdir** The mkdir(make directory) command allows users to create directories or folders.

   ```bash
   $ mkdir ubuntu
   $ ls
   ubuntu
   ```

   The option '-p' is used to create multiple directories or parent directories at once.

   ```bash
   $ mkdir -p dir1/dir2/dir3
   $ cd dir1/dir2/dir3
   ~/Desktop/Linux/dir1/dir2/dir3$
   ```

4. **rmdir**: The rmdir(remove directories) is used to remove _empty_ directories. Can be used to delete multiple empty directories as well. Safer to use compared to `rm -r FolderName`. This command can also be forced to delete non-empty directories.

   1. Remove empty directory:

   ```bash
   rmdir FolderName
   ```

   2. Remove multiple directories:

   ```bash
   rmdir FolderName1 FolderName2 FolderName3
   ```

   3. Remove non-empty directories:

   ```bash
   rmdir FolderName1 --ignore-fail-on-non-empty
   ```

   4. Remove entire directory tree. This command is similar to `rmdir a/b/c a/b a`:

   ```bash
   rmdir -p a/b/c
   ```

5. **rm**: The rm(remove) command is used to remove objects such as files, directories, symbolic links etc from the file system.
   1. Remove file: The rm command is used to remove or delete a file
   ```bash
   rm file_name
   ```
   2. Remove file forcefully: The rm command with -f option is used for removal of file without prompting for confirmation.
   ```bash
   rm -f filename
   ```
   3. Remove directory: The rm command with -r option is used to remove the directory and its contents recursively.
   ```bash
   rm -r myDir
   ```
   4. Remove directory forcefully: The rm command with -rf option is used to forcefully remove directory recursively.
   ```bash
   rm -rf myDir
   ```
6. **touch**: The touch command is is used to create, change and modify timestamps of a file without any content.
   1. **Create a new file:** You can create a single file at a time using touch command. The file created is an empty file.
       ```bash
       touch file_name
       ```
   2. **Create multiple files:** You can create the multiple numbers of files at the same time.
       ```bash
       touch file1_name file2_name file3_name
       ```
   3. **Change access time:** The touch command with `a` option is used to change the access time of a file.
       ```bash
       touch -a file_name
       ```
   4. **Change modification time:** The touch command with `m` option is used to change the modified time.
       ```bash
       touch -m file_name
       ```
   5. **Use timestamp of other file:** The touch command with `r` option is used to get timestamp of another file.
       ```bash
       touch -r file2 file1
       ```

       In the above example, we get the timestamp of file1 for file2.

   6. **Create file with Specific time:** The touch command with 't' option is used to create a file with specified time.
       ```bash
       touch -t 1911010000 file_name
       ```
7. **cat**: The cat command is used to create single or multiple files, view contain of file, concatenate files and redirect output in terminal or files.
     ```bash
     $ cat [OPTION] [FILE]...
     ```
   1. **Create a file:** Used to create a file with specific name, content and press exit using `CTRL + D`
       ```bash
       cat > file_name1.txt
       Hello, How are you?
       ```
   2. **View file contents:** You can view contents of a single or more files by mentioning the filenames.

       ```bash
       cat file_name1 file_name2
       ```
   3. **More & Less options:** If a file having a large number of content that won’t fit in the output terminal then `more` & `less` options can be used to indiate additional content.

       ```bash
       cat file_name1.txt | more
       cat file_name1.txt | less
       ```

**[⬆ Back to Top](#table-of-contents)**

### File permissions

Since Linux is a multi-user operating system, it is necessary to provide security to prevent people from accessing each other’s confidential files.
So Linux divides authorization into 2 levels,

1. **Ownership:**
Each file or directory has assigned with 3 types of owners
i. **User:** Owner of the file who created it.
ii. **Group:** Group of users with the same access permissions to the file or directory.
iii. **Other:** Applies to all other users on the system

2. **Permissions:**
Each file or directory has following permissions for the above 3 types of owners.

    i.   **Read:** Give you the authority to open and read a file and lists its content for a directory.

    ii.  **Write:** Give you the authority to modify the contents of a file and add, remove and rename files stored in the directory.

    iii. **Execute:** Give you the authority to run the program in Unix/Linux.

     The permissions are indicated with below characters,

         r = read permission

         w = write permission

         x = execute permission

         \- = no permission

    The above authorization levels represented in a diagram

<img src="https://github.com/appsec-samurai/World-of-Linux/blob/master/Images/linux_permissions.png" width="600" height="400">

There is a need to restrict own file/directory access to others.

**Change access:**
The `chmod` command is used to change the access mode of a file.  This command is used to set permissions (read, write, execute) on a file/directory for the owner, group and the others group.

```cmd
chmod [reference][operator][mode] file...

Example
chmod ugo-rwx test.txt
```

There are 2 ways to use this command,

1. **Absolute mode:**
The file permissions will be represented in a three-digit octal number.

     The possible permissions types represented in a number format as below.

     | Permission Type | Number |  Symbol |
     | ------------- | ----- | ----- |
     | No Permission | 0 | --- |
     | Execute | 1 | --x |
     | Write | 2 | -w- |
     | Execute + Write | 3 | -wx |
     | Read | 4 | r-- |
     | Read + Execute | 5 | r-x |
     | Read + Write | 6 | rw- |
     | Read + Write + Execute | 7 | rwx |


Let's update the permissions in absolute mode with an example as below,

   ```cmd
    chmode 764 test.txt
   ```

2. **Symbolic mode:**
In the symbolic mode, you can modify permissions of a specific owner unlike absolute mode.

    The owners are represented as below,

     | Owner | Description |
     | ----- | ----- |
     | u | user/owner |
     | g | group |
     | o | other |
     | a | all |

    and the list of mathematical symbols to modify the file permissions as follows,

     | Operator | Description |
     | ------------- | ----- |
     | + | Adds permission |
     | - | Removes the permission |
     | = | Assign the permission |

**Changing Ownership and Group:**
It is possible to change the the ownership and group of a file/directory using `chown` command.

```cmd
chown user filename
chown user:group filename

Example:
chown John test.txt
chown John:Admin test.txt
```

**Change group-owner only:**
Sometimes you may need to change group owner only. In this case, chgrp command need to be used

```cmd
chgrp group_name filename

Example:
sudo chgrp Administrator test.txt
```

**[⬆ Back to Top](#table-of-contents)**

### Networking

1.  **Display network information:** `ifconfig` command is used to display all network information(ip address, ports etc)

```cmd
ifconfig -a
```

2.  **Test connection to a remote machine:** Send an echo request to test connection of a remote machine.

    ```cmd
    ping <ip-address> or hostname

    Example:
    ping 10.0.0.11
    ```

3.  **Show IP Address:** Display ip address of a currennt machine

    ```cmd
    hostname -I
    (OR)
    ip addr show
    ```

4.  **Active ports:** Shows active or listening ports

     ```cmd
     netstat -pnltu
     ```

5.  **Find information about domain:** `whois` command is used to find out information about a domain, such as the owner of the domain, the owner’s contact information, and the nameservers used by domain.

    ```cmd
    whois [domain]

    Example:
    whois google.com
    ```

**[⬆ Back to Top](#table-of-contents)**

### Installing packages

1. **Install package:**

```cmd
yum install package_name
For Ubuntu distributions:
sudo apt install <package path>
```

2. **Package description:**
The info command is used to display brief details about a package.

```cmd
yum info package_name
```

3. **Uninstall package:**
The remove command is used to remove or uninstall package name.
```cmd
yum remove package_name
For Ubuntu distributions:
sudo apt remove package_name
```
4. **Install package from local file:**

It is also possible to install package from local file named package_name.rpm.

```cmd
rpm -i package_name.rpm
```

5. **Install from source code:**

```cmd
tar zxvf sourcecode.tar.gz
cd sourcecode
./configure
make
make install
```

**[⬆ Back to Top](#table-of-contents)**

### Disk usage

1.  **Synopsis:** `du` command is used to check the information of disk usage of files and directories on a machine

```cmd
du [OPTION]... [FILE]...
```

2.  **Disk usage of a directory:** To find out the disk usage summary of a /home/ directory tree and each of its sub directories

```cmd
du  /home/
```

3.  **Disk usage in human readable format:** To find out the disk usage in human readable format

```cmd
du  -h /home/
```

4.  **Total disk usage of a directory:** To find out the total disk usage

```cmd
du  -sh /home/
```

5.  **Total disk usage of all files and directories:** To find out the total disk usage of files and directories

```cmd
du  -ah /home/
```

6.  **Total disk usage of all files and directories upto certain depth:** print the total for a directory only if it is N or fewer levels below the command

```cmd
du  -ah --max-depth 2 /home/
```

7.  **Total disk usage with excluded files:** To find out the total disk usage of files and directories, but excludes the files that matches given pattern.

```cmd
du -ah --exclude="*.txt" /home/
```

8.  **Help:** This command gives information about `du`

```cmd
du  --help
```

**[⬆ Back to Top](#table-of-contents)**

### Search Files

1. **Pattern search:**
The `grep` command is used to search patterns in files.

```cmd
grep pattern files
grep -i // Case sensitive
grep -r // Recursive
grep -v // Inverted search

Example:
grep "^hello" test.txt // Hello John
grep -i "hELLo" text.txt // Hello John
```

2. **Find files and directories:**

The `find` command is used to find or search files and directories by file name, folder name, creation date, modification date, owner and permissions etc and perform subsequent operations on them.

i. **Search file with name:**

```cmd
find ./directory_name -name file_name

Example:
find ./test -name test.txt // ./test/test.txt
```

ii. **Search file with pattern:**

```cmd
find ./directory_name -name file_pattern

Example:
find ./test -name *.txt // ./test/test.txt
```

iii. **Search file with executable action:**

```cmd
find ./directory_name -name file_name -exec command

Example:
find ./test -name test.txt -exec rm -i {} \; // Search file and delete it after confirmation
```

iv. **Search for empty files or directories:**

The find command is used to search all empty folders and files in the entered directory or sub-directories.

```cmd
find ./directory_name -empty

Example:
find ./test -empty
//./test/test1
//./test/test2
//./test/test1.txt
```

v. **Search for files with permissions:**

The find command is used to find all the files in the mentioned directory or sub-directory with the given permissions

```cmd
find ./directory_name -perm permission_code

Example:
find ./test -perm 664
```

vi. **Search text within multiple files:**

```cmd
find ./ -type f -name file_pattern -exec grep some_text  {} \;

Example:
find ./ -type f -name "*.txt" -exec grep 'World'  {} \; // Hello World
```

3. **Whereis to locate binary or source files for a command:**
The whereis command in Linux is used to locate the binary, source, and manual page files for a command. i.e, It is used to It is used to find executables of a program, its man pages and configuration files.

```cmd
whereis command_name

Example:
whereis netstat //netstat:  /bin/netstat /usr/share/man/man8/netstat.8.gz(i.e, executable and location of its man page)
```

4. **Locate to find files:**
The locate command is used to find the files by name. This command is faster compared to find command because it searches database for the filename instead of searching your filesystem.

```cmd
locate [OPTION] PATTERN

Example:
locate "*.txt" -n 10 // 10 file search results ending with .txt extension
```

**[⬆ Back to Top](#table-of-contents)**

### SSH

SSH (Secure Shell) is a network protocol that enables secure remote connections between two systems.

1.  **Connect remote machine using IP address or machine name:** The remote server can be connected with local user name using either host name or IP address

```cmd
ssh <host-name> or <ip-address>

Example:
ssh 192.111.66.100
ssh test.remoteserver.com
```

2.  **Connect remote machine using username:** It is also possible specify a user for an SSH connection.

```cmd
ssh username@hostname_or_ip-address

Example:
ssh john@192.0.0.22
ssh john@test.remoteserver.com
```

3.  **:Connect remote machine using custom port** By default, the SSH server listens for a connection on port 22. But you can also specify the custom port.

```cmd
ssh <host-name> or <ip-address> -p port_number

Example:
ssh test.remoteserver.com -p 3322
```

4.  **Generate SSH keys using keygen:** SSH Keygen is used to generate a key pair which consists of public and private keys to improve the security of SSH connections.

```cmd
ssh-keygen -t rsa
```

5.  **Copying SSH keys to servers:** For SSH authentication, `ssh-copy-id` command will be used to copy public key(id_rsa.pub) to server.

```cmd
ssh-copy-id hostname_or_IP
```

6.  **Copy a File Remotely over SSH:** SCP tool is used to securely copy files over the SSH protocol.

```cmd
scp fileName user@remotehost:destinationPath

Example:
scp test.txt test@10.0.0.64:/home/john/Desktop
```

7.  **Edit SSH Config File** SSH server options customized by editing the settings in `sshd_config` file.

```cmd
sudo vim /etc/ssh/sshd_config
```

8.  **Run commands on a remote server** SSH commands can be executed on remote machine using the local machine.

```cmd
ssh test.remoteserver.com mkdir NewDirectoryName // Creating directory on remote machine
```

9.  **Restart SSH service:** You need to restart the service in Linux after making changes to SSH configuration.

```cmd
sudo ssh service restart
(or)
sudo sshd service restart
```

**[⬆ Back to Top](#table-of-contents)**

### Vi/Vim-commands

Vi editor is the most popular text editor from the early days of Unix. Whereas Vim(Vi IMproved) is an improved version of vi editor to be used in CLI (command line interface) for mainly text editing tasks in many configuration files. Some of the other alternatives are Elvis, Nvi, Nano, Joe, and Vile.
It has two main operation modes,

1.  **Command Mode:** It allows the entry of commands to manipulate text.
2.  **Entry mode(Or Insert mode):** It allows typed characters on the keyboard into the current file.

#### 1. Start with Vi Editor

You can create a new file or open an existing file using `vi filename` command.

```cmd
 vi <filename_NEW> or <filename_EXISTING> // Create a new file or open an existing file

 Example:
 vi first.txt
```

Let's see how do you create file, enter the content and leave the CLI by saving the changes.

1.  Create a new file named `first.txt`
2.  Press `i` to enter the insert mode
3.  Enter the text "Hello World!"
4.  Save the text and exit by pressing `:wq!` command
5.  Check the entered text

#### 2. Cursor movement

    These commands will be used in Command mode.

##### Move cursor

You can use arrow keys(left, right, up and down) to move the cursor on the terminal. But you can also other keys for this behavior.

```cmd
 h        # Move left
 j        # Move down
 k        # Move up
 l        # Move right
```

##### Jump one word

These commands used to jump one word at a time

```cmd
w        # Jump forwards to the start of a word
W        # Jump forwards to the start of a WORD
e        # Jump forwards to the start of a word
E        # Jump forwards to the start of a WORD
b        # Jump backwords to the start of a word
B        # Jump backwords to the start of a WORD
```

##### Jump to start or end of a line or next line

These commands used to jump starting or ending of a line or a next line.

```cmd
^        # Jump to the start of a current line
$        # Jump to the end of a current line
return   # Jump to the start of a next line
```

##### Move sides

These commands used to moves all sides of the screen

```cmd
Backspace # Move cursor one character to the left
Spacebar  # Move cursor one character to the right
H(High)   # Move cursor to the top of the screen
M(Middle) # Move cursor to the middle of the screen
L(Low)    # Move cursor to the bottom of the screen
```

##### Paging and Scrolling

Paging is used to moves the cursor up or down through the text a full screen at a time. Whereas Scrolling happens line by line.

```cmd
Ctrl + f     # move forward one full screen
Ctrl + b     # move backward one full screen
Ctrl + d     # move forward half a screen
Ctrl + u     # move backward half a screen
```

##### Inserting Text

These commands places vi in entry mode from command mode. First, you need to be in command mode to use the below commands.

###### Insert

```cmd
i    # Insert text to the left of the cursor
I    # Insert text at the beginning of a line
ESC  # Exit insert mode
```

###### Append

```cmd
a    # Insert(or Append) text to the right of the cursor
A    # Insert(or Append) text at the end of a line
```

###### Open a line

```cmd
o    # Open a line below the current cursor position
O    # open a line above the current cursor position
```

##### Editing Text

1. **Change word:** Change word/part of word to right of cursor

    ```cmd
    cw
    ```

2. **Change line** Change entire line

    ```cmd
    cc
    ```

3. **Change line from specific character** Change from cursor to end of line

    ```cmd
    C
    ```

##### Deleting Text

1. **Deleting One Character:** Position the cursor over the character to be deleted and type x

    ```cmd
    x
    X       //To delete one character before the cursor
    ```
2. **Deleting a Word:** Position the cursor at the beginning of the word and type dw

    ```cmd
    dw
    ```
3. **Deleting a Line:** Position the cursor anywhere on the line and type dd.

    ```cmd
    dd
    ```

##### Cut, Copy & Paste

   Copy, Cut and Paste operations can be done in either Normal or visual Mode.

1. **Normal mode:** This mode appears on click of `Esc` key.

   **Copy** There are various copy or yank commands based on amount of text to be copied. The `y` character is used to perform this operation.

   i. Copy an entire line: Just place the cursor at the beginning of the line and type `yy`

   ```cmd
   yy
   ```

   ii.Copy three lines: Just place the cursor from where to start copying and type `3yy`

   ```cmd
   3yy
   ```

   iii. Copy word with trailing whitespace: Place the cursor at the beginning of the word and type `yaw`

   ```cmd
   yaw
   ```

   iv. Copy word without trailing whitespace: Place the cursor at the beginning of the word and type `yiw`.

   ```cmd
   yiw
   ```

   v. Copy right of the cursor: Copy text right of the cursor to the end of line using `y$` command

   ```cmd
   y$
   ```

   vi.Copy left of the cursor: Copy text left of the cursor to the end of line using `y^` command

   ```cmd
   y^
   ```

   vii. Copy text between the cursor and character: Copy text between the cursor and specified character.

   ```cmd
   ytx(Copy until x and x is excluded)
   yfx(Copy until x and x is included)
   ```

   **Cut** There are various cutting or deleting commands based on amount of text to be deleted. The `d` character is used to perform this operation.

   i. Cut entire line: Cut the entire line where the cursor is located

   ```cmd
   dd
   ```

   ii.Cut three lines: Cut the three lines starting from the place where cursor is located

   ```cmd
   3dd
   ```

   iii.Cut right of the cursor: Cut the text from the right of the cursor till the end of line

   ```cmd
   d$
   ```

   iii.Cut left of the cursor: Cut the text from the left of the cursor till the beginning of line

   ```cmd
   d^
   ```

   **Paste** This operation is performed using `p` command to paste the selected text

   ```cmd
   p
   ```

2. **Visual Mode** In this mode, first select the text using below keys

    1. v (lowercase): To select individual characters
    2. V (uppercase): To select the entire line
    3. Ctrl+v: To select by block

    and perform copy, cut and paste operations using y,d and p commands

##### Exiting

    These commands are used to exit from the file.
    ```cmd
    :w	    # Write (save) the file, but don't exit
    :wq	    # Write (save) and quit
    :wq!	  # Force write (save) and quit
    :q	    # Quit, but it fails if anything has changed
    :q!	    # Quit and throw away for any changes
    ```

**[⬆ Back to Top](#table-of-contents)**
