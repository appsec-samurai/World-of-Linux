# *****Linux-Commands*****

### Table of Contents

---

| No. | Topic                                                                   |
| --- | ----------------------------------------------------------------------- |
| 1   | [**System information**](#system-information)
| 2	  | [**Hardware information**](#hardware-information)	
| 3	  |	[**User information**](#user-information)                               |
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

15.  ** Check `Linux File System` Information.

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

7. **grep:** It  is a powerful pattern searching tool to find information about a specific user from the system accounts file: /etc/passwd.

	```bash
    $ grep -i appsec-samurai /etc/passwd
    appsec-samurai:x:1000:1000:appsec-samurai:/home/appsec-samurai:/bin/bash
    ```

8. **W Command:** It(W) is a command-line utility that displays information about currently logged in users and what each user is doing.

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

