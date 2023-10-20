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
| 9   | [**System and Hardware information**](#system-and-hardware-information) |
| 10  | [**Search Files**](#search-files)                                       |
| 11  | [**SSH**](#ssh)                                                         |
| 12  | [**Vi/Vim-commands**](#vi/vim-commands)                                 |

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
