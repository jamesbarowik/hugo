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
draft: true
---
## Introduction
To further my career and learning, and the installation of the Raspberry Pi Cluster. I looked into creating a bash script, that would automate the process as much as possible to reduce the amount of time that it took to setup and install all of the machines. Something that I would like to look into in the future is the addition of a deployment server that install the OS automatically across the network of machines. I currently have no idea how I’d go about doing that so using a bash based automated process.

I checked around for other examples of bash scripting and bash found similar things to what I was doing, The first time I tried to do this I had the files on a USB Stick which was a lot slower as the file transfer was much slower than the internet speed.
## Commands
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
