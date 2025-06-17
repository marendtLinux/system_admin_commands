## File System

### lsblk-command

show a list of all block devices
```bash
lsblk
```

example output
```bash
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 238,5G  0 disk 
├─sda1   8:1    0     1G  0 part /boot/efi
└─sda2   8:2    0 237,4G  0 part /
```

Output explanation:

**NAME** sda is the name of the first hard drive, sdb would be the second and so forth
the partitions of a hard drive a then numbered: sda1, sda2

**MAJ** (Major) shows the device driver (8 is usualy the number for the first hard disk)

**MIN** (Minor) shows the specific device or partition within the major device

**RM 0**  is not a removale media like an usb stick

**RO 0** is not READ-ONLY

**TYPE** disk is a hard drive, part stand for partition

**MOUNTPOINTS** where the device is mounted on the file system

show the corresponding device files on /dev:
```bash
ls -l /dev/sda*
```

### inspection


show a list of all devices
```bash
ls -l /dev
```

show information on the file system
```bash
df -h
```
show used types of the file system
```bash
df -T
```

show information on the file system with better overview
```bash
duf
```

show information like UUID to a device file, here for example /dev/sda2
```bash
blkid /dev/sda2
```

### /etc/fstab and /etc/mtab

show contents of fstab and mtab, columnt -t option can be used for better readability
```bash
cat /etc/fstab
cat /etc/mtab | column -t
```

- fstab and mtab use the same syntax
- fstab contains all mounted filesystem at boot time
- mtab contains all currently mounted filesystem, hence it can include filesystems mounted after boot time

#### Syntax of fstab and mtab 

- each line describes a file system
- a line contains six columns. They contain the following information:

1. device name (can also be the uuid)
2. mount point, on which the device is mounted on
3. type of file system (e.g. ext4, btrfs)
4. mount-Options (e.g. defaults: no options selected, ro:read-only, noexec:no programm execution allowed)
5. contains information for the program dump and is ignored by the linux os otherwise
6. order, in which the file systems are being checked when booting. 1 often stands for the
system partition and 0 for all else, which means they are not checked. 

example output from fstab:
```bash
/dev/disk/by-uuid/573ebbaa-4466-4caa-9a92-7e22432456b5 / ext4 defaults 0 1
```

### formatting a usb stick

list usb device with lsblk, usb device has value 1 at column RM (removable)
```bash
lsblk
```

In this examble the usb device is sdb and has two partitions: sdb1 and sdb2.

The column MOUNTPOINTS from lsblk shows, that sdb2 is mounted. Before formatting, the 
partition needs to be unmounted:

```bash
umount /dev/sdb2
```

delete usb drive and create a new partition table of typ gpt
```bash
parted /dev/sdb mklabel gpt
```

now we edit the partition table by creating a primary
partition with fat32 and define the starting and ending point
at 1mib. the fat32 is not actually created, is just a 
information in the partition table
```bash
parted /dev/sdb 'mkpart primary fat32 1mib -1mib'
```

now we create the actual file system with the name USB_DATA
```bash
mkfs.vfat -F 32 -n USB_DATA /dev/sdb1
```

at last we can mount the new file system, /media/data has to be
and existing directory
```bash
mount /dev/sdb1 /media/data
```

