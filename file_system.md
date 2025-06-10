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

show information on the file system with better overview
```bash
duf
```


















