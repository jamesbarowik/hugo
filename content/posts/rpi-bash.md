---
title: "Raspberry Pi Bash Project"
date: 2024-07-28
url: /rpi5-bash 
image: https://github.com/SilentSmeary/hugo/blob/master/images/posts/2024/raspberry-pi-5.png?raw=true
categories:
  - Raspberry Pi 5
  - Linux
  - Automation
series:
 - 2024 
---
## Introduction:
To further my career and learning, and the installation of the Raspberry Pi Cluster. I looked into creating a bash script, that would automate the process as much as possible to reduce the amount of time that it took to setup and install all of the machines. Something that I would like to look into in the future is the addition of a deployment server that install the OS automatically across the network of machines. I currently have no idea how I’d go about doing that so using a bash based automated process.

I checked around for other examples of bash scripting and bash found similar things to what I was doing, The first time I tried to do this I had the files on a USB Stick which was a lot slower as the file transfer was much slower than the internet speed.

I made sure that i added a .gitignore to remove and files that weren't required during the running of the script, this is to reduce the size of the repo to increase the cloning speed to setup the initial script and ensure that everything is running correctly.

I also added the local-downloads folder to ensure that any files that were downloaded or creating during to script running were in the local-downloads folder and were removed after as to reduce machine lag and free space on the drive for the users

**The script firstly remove software;**
- QT Transmission
- Remmina
- Gnome Snapshot
- Rythmbox

**The script installs software;** 
- thonny
- pandas (python library)
- Chromium Browser
- Okular
- Git
- GitHub Desktop
- PhpStorm
- Project Libre
- apache
- php
- sssd-ad
- sssd-tools
- realmd
- adcli

## Commands:
These are a few of the basic commands that i used with a brief notes about what they do, from a very basic understanding

### apt
```
sudo apt update
sudo apt upgrade
```
Basic package manager for debian based systems, I opted to change this out for an expanded and quicker manager called nala that can be up to 16x faster then APT.

### wget
```
sudo wget "https://github.com/fastfetch-cli/fastfetch/releases/download/2.18.1/fastfetch-linux-amd64.deb"
```
The wget command is used to download a file from a web server and download it to the local drive, this is much quicker than using the USB stick to download the files.

### nmcli
```
sudo nmcli connection modify 'tlevel-digital' ipv4.dns "172.16.0.4 8.8.8.8"
sudo nmcli connection modify 'tlevel-digital' ipv4.ignore-auto-dns yes
```
The use of the Network Manager CLI to automate the process of the DNS Server to ensure, The initial idea of this would have been to have it hand it out via DHCP, But the AP that we had doesn't support the altering of the DHCP Pool without an addon that was more than what we required so we opted to manually get it up instead.

### grep
```
nmcli connection show tlevel-digital | grep ipv4.dns:
```
The connections show listed all the information about the selected network, the addition of grep was to filter the output as there was lots of additional information that isn't required for the setup of these machines, as they aren't required to have a statically assigned to each machine.

### dpkg
```
sudo dpkg -i projectlibre_1.9.3-1.deb
```
dpkg is a Debian based command line tool to install .deb files on the system this is used for a few of the packages that have been installed.

## File Types:
### .desktop
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/opt/PhpStorm/bin/phpstorm.sh
Name=PhpStorm
Comment=Jetbrains PHP IDE
Icon=/opt/PhpStorm/bin/phpstorm.png
```
A .desktop file is the way that you are supposed to add new applications to the gnome start menu as the Machines are using Ubuntu, it is important for users that are too familiar with linux to be able to use the start menu to open and locate common software. The example that was shown above is for PhpStorm, another features that I am in the middle of implementing is phpmyAdmin so that the users are able to select the phpmyAdmin site without needing to know the IP address of the server that is running phpmyAdmin as we aren't running that locally on the Pi's as they aren't that powerful. The post will be updated in the future to add more and more features that I have added.

## Final Script:
https://github.com/SilentSmeary/rpi-bash

## Usage:
```sh
git clone https://github.com/silentsmeary/rpi-bash
cd rpi-bash
./setup.sh
```