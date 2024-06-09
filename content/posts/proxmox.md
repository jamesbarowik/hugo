---
title: "Proxmox"
date: 2024-04-17
url: /proxmox
image: https://github.com/SilentSmeary/SilentSmeary/blob/main/images/hugo/proxmox.jpg?raw=true
categories:
  - Linux
  - Servers
  - Networking
  - KVM
  - Virtual Machines
series:
 - 2023 
draft: false
---
## Introduction
Firstly, we installed Windows Server 2019 on the bare metal. As I wanted to learn more skills related to infrastructure it was essential that I could learn linux skills as well as windows skills. So, I spent a few days looking around at other solutions that ment I was able to learn more with the hardware and I stumbled across Proxmox.

Proxmox is a free and open source solution to virutalisation that allows for the creation of virtual machines using any operating system. Which ment we could host our Active Directory Service, Aswell as the networked storage solution that we use TrueNAS Scale.

## Installation
The installation was very easy as the Graphical Installer was very simple and needed the basic amount of information to install fully. I made sure to give the server a Static IP as if it used a DHCP IP the lease could end and it might not be given the same IP. Meaning that the server is inaccessible

## VM's
We used Windows Server 2019 as it worked with the bare metal hardware to make sure that I didn't run into any issues later. We need to use windows for the Active Directory to authenticate users.

We need a central server for storing files to ensure that users aren't storing files on there Local Machines incase Machines were re-imaged and users didn't backup there files to the cloud. We used TrueNAS Scale for this to secure the files behind user accounts

## Server Hardware
- 192GB RAM
- 2x CPU 12 Cores Each
- 2 x 1GB On Board Networking
- 6x SATA Drive Days
- Fujitsu PCIE Raid Card
- 1x 240GB Kingston SSD 
- 5x 480GB Kingston SSD