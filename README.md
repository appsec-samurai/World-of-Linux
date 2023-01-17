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
