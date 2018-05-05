---
title: rsync-note
tags: [rsync,note]
---

sudo rsync -aHAXv --delete -n --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/* --exclude=/run/* --exclude=/cdrom/* --exclude=/mnt/* --exclude=/media/* --exclude="swapfile" --exclude="lost+found" --exclude=".cache" --exclude="venv" --exclude="Android" --exclude="JetBrains" --exclude="Steam" --exclude="android-studio" --exclude="PycharmProjects" --exclude=".cxoffice" --exclude="VirtualBox VMs" --exclude=".AndroidStudio3.0" --exclude="Downloads" --exclude=".PyCharm2018.1" / /media/watmel/SanDisk/Ubuntu1604

sudo mkdir /mnt/usb
sudo mkdir /mnt/system
lsblk
sudo mount /dev/sdxx /mnt/system
sudo mount /dev/sdxx /mnt/usb

time sudo rsync -aHAXv --delete-after -n  --exclude=/mnt/* --exclude="swapfile" --exclude="lost+found" --exclude="/etc/fstab" /mnt/usb/Ubuntu1604/ /mnt/system/

sudo update-grub
sudo apt-get remove nvida-*   #解决图形界面输入正确密码无法登陆

