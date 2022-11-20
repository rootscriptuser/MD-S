---
title: linux tutorial By Nuggets @ FreeCodeCamp
---

# BIOS && UEFI

* basic input output sys
* unified extensible firmware interface

* mbr = master boot record (ha?)
* UEFI code is on a special partition 
* BIOS is not on a special partition
* secure boot (UEFI)


# GRUB GRUB2

* grand unified 
* boot the computer

## GRUB LEGACY

* menu.lst
* difficult to config

## GRUB 2
* grub.cfg
* /etc/default/grub
* can boot USB UUID , dvice
* press shift (hidden boot menu
* sudo update-grub (update grub config)

# boot methods

* PXE, USB CD, iPXE, ISO
* hardware vs software
* iPXE = uses http instead SFTP to dowload software
* PXE = pre-boot 

# boot proces

1. BIOS or UEFI
1. GRUB or GRUB2
    * initrd (driver info to access kernel)
1. vmlinux (linuz cmprss) == base kernel
    * initramFS (filesys to load in ram, along kernel)
    * dracut
1. full kernel 
    * mods

> $ ls /boot
> $ ls /lib/modules


# kernel panic

* when u update linux
* when updating linux keeps old kernel
* select an older kernel version

> grub menu SHIFT
> select kernel (older)

* loading
* blacklisting
* config file

> $ vim /etc/modules
> $ vim  /etc/modprobe.d/ ***blacklisting***

* insmod, rmmod
* madprobe , lsmod
* depmod

* INSMOD (no dep check, full path=
* MODPROB (advanced , by mod name, install dep)

# networking

> $ ip route
> $ netstat route
> $ ip add 
> $ dig
> $ nslookup
> $ ping
> $ dig @DnsServerIP HostIP
> $ cat /etc/hosts

# network config files

## ubuntu
> $ /etc/hosts (fist resort for DNS )
> $ /etc/nsswitch.conf
> $ /etc/resolv.conf (nameserver) 
> nameserver (local cashing dns maybe)
> $ /etc/network/interfaces
> $ /etc/netplan (newer config file  YAML)
> $ sudo netplan apply

## network bonding modes

* switch support
* generic
* use multiple cables for one connection

### Mode 0-6

1. balance -rr  (crosswire no switch supp) MODE 0
1. active backup (only one port active at once)
1. balance -xor (hash for port and next host)
1. broadcast 
1. 802.3ad ( industry standard link aggregation !!! MODE 4)
1. balance -tlb
1. balance -alb (always switches MAC Addres)

> most used 0 4 and 6 !!!

> $ cat /proc/net/bonding

# GPT && MBR

* GPT newer
* protective MBR
* GUID partition table => GPT
* Master Boot Record


## MBR 

* /dev/sda (defines what is what on / reference)

## GPT

* table of content ( on multiple places on disk)
* bigga drives than 2TB

# Linux FIle sys

* one giant filesys hierarchy
* trasversing 

* real virtual
* relative vs absolute
* network mounts

* new disk is a file inside root filesys
 
# Partitions

* parted
* gparted
* fdisk

> $ lsblk

1. created new parittion table (GPT, MBR, DOS)
1. create partition

## Formating partitions

* ext (journals)
* xfs (old)
* btrfs 
* dos (nfts, fat32, vfat)

* ext2
* ext3
* ext4 (wiledly used)

> `$ mkfs.ext4 path `
> $ /ect/fstab ( edit to mount at boot partition)
> $ mount -a (mount all in fstab)

> $ tune2fs
> $ fsck
> scan automaticlly the filesys at boot 
> to be scanned needs to be unmounted 
