---
layout: page
title: Projects
permalink: /projects/
---
## 2024
- [Google Cybersecurity Certification](https://1dgk.github.io/2024/01/24/gcc-course-index.html)
- [How to Manage File Permissions in Linux](https://1dgk.github.io/2024/02/18/file-permissions-in-linux.html)

## Home Lab / Self Host
**Linux Permissions fix for Plex and/or Jellyfin**

Fix permissions to allow Plex to access /media/$USER

Check which group you and plex belong to:
```bash
groups
groups plex
```
Now, add plex user to your user group, and allow this group to access /media/$USER:
```bash
MYGROUP="$USER"
sudo usermod -a -G $MYGROUP plex
sudo chown $USER:$MYGROUP /media/$USER
sudo chmod 750 /media/$USER
sudo setfacl -m g:$MYGROUP:rwx /media/$USER
sudo service plexmediaserver restart
```
Credit to KrisWebDev from [askubuntu](https://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions)

