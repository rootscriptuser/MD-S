# RaspberryPi transsmision container

> commands to sistematiclly install docker as root, make a macVlan for container on separate local IP and permanentlly mount a external HD drive

## install and update packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install tmux vim curl git uidmap -y
```

## set .bashrc and .vimrc
```
touch .vimrc
echo "set rnu" >> .vimrc
echo "set cursorline" >> .vimrc
echo "set tabstop=2" >> .vimrc

echo "set -o vi" >> .bashrc

```

## install docker with script as SUDO

```bash
curl https://get.docker.com/ >> install-docker.sh
sudo install-docker.sh

```

## TO-DO install docker rootles

> TO-DO set permisionss for files etc.

```
cd /usr/bin/
dockerd-rootless.setptool.sh install
```
## remove docker installed  with script

```
sudo apt-get purge docker-ce
sudo rm -rf /var/lib/docker

```

## Mounting WD elemnts external HD disk

```bash
#Find the drive (in our case /dev/sda1)
sudo fdisk -l
#install NTFS-3g
sudo apt-get install ntfs-3g
#Make the mount directory and manage it's owner
sudo mkdir /media/pidrive
sudo chown pi:pi /media/pidrive
#Mount the drive
sudo mount -t ntfs-3g -o uid-pi,gid-pi /dev/sda1 /media/pidrive
#Now you're done but it's not permanent

#Making it permanent
#Edit file system table
sudo nano /etc/fstab

#Add this line of text after the SD card partitions
/dev/sda1	/media/pidrive	ntfs-3g	uid=pi,gid=pi	0	0
#hit ctrl-o to save and ctrl-x to exit nano

#Now the mounting will be restored on reboot
#Reboot to test it
sudo shutdown -r now 

```


# spin up cnt with docker compose and make a network macvlan
```
curl COMPOSEFILE
mkdir transmission
cd transmission
sudo docker compose up -d
```
