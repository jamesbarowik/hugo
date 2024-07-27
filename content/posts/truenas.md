---
title: "TrueNAS Scale"
date: 2024-01-20
url: /truenas
image: https://github.com/SilentSmeary/hugo/blob/master/images/posts/2024/truenas.png?raw=true
categories:
  - Linux
  - TrueNAS
series:
 - 2024 
---
## Introduction
We needed a safe fast and secure solution for storage. We need a solution that supported both Windows Shares (SMB) and Linux Shares. With the requirements that we need and the hardware that we have the search began. For the OS that was compatible with our older hardware and that worked with never drives that were harvested from our old college machines that were no longer in use.

## Final Choice
After a few days searching and countless failed attempts to deploy a working server we found TrueNAS Scale and Core. After looking into the documentation for both of them. We found that it was not viable for use TrueNAS Scale as it ment we needed two boot drives this would have made the machines more redundant incase of a drive failure. For a long term solution this would have been much more viable. But we didnt not have the drive bays aviable for the space that we wanted. As the server only had 6 bays we decided to go for the TrueNAS Core which required us to have one boot drive. Which was perfect for our situation.

## Hardware Specs
The server chasis is a Fujitsu RX300 S7. On the front of the server there are 6 SATA ports in the front of the server. That are connect with a SAS connected to the PCIE Raid Card on the motherboard. The server has two CPUs both Intel Xeon E5-2620 with 12 cores and 24 threads. We decided to make the server have as much memory as we had available this was to make sure that we were able to set the RAM and the primary cache so that the drives could handle the max efficenty psible and always be running and handling data the fastest possible speed. 192GB DDR3 1066 mhz memory.

## Installation Process
For more information about installation
https://www.truenas.com/docs/

The installation process was mostly normal there was no major hickups with the installation. Once the OS was installed the first hurdle was fighting with the network card. I wanted to make sure that we had the fastest Network Card to make sure that users were able to upload larger files at the the same time and not stress the network attempting the tasks. The servers came with the added network card by standard when they arrvied. We had the 2 ports that were standard to the motherboard, there was then two ports that were added with one of the extra network cards. We had another network card that added four more ports. There was one more network card that added two SFP ports. that we were not set up to use effectively so I decided to take that extra card out of the server to reduce the slots that showed up on there already. From there it was configurating the network, I had assigned the Static IP to the required port and made sure that the port was given the network by checking the network link lights on the network card. They were both flashing to indicate that the network was connected and authenticated. I attempted to connect to the website and recived the first error of the day. The IP was inaccessable. From there we spent some timeW attempting to fix the network errors with no outcome we decided that the best choice was to setup a DHCP pool on our VLAN to get DHCP to hand out and IP to give us the correct networking information, which allowed for straight connection. This allowed for us to make the connection and then change the IP on the socket to be a Static IP to make deployment much easier

## Storage Drives
- 1x 240GB Kingston SSD [BOOT]
- 5x 480GB Kingston SSD [STORAGE] 

Our goal was to have two storage clusters. One that was for the private share and the other that was the public share. In the first server that we deployed we completed this and made two addressable storage drives.

The private share that had a little bit over 1.2TB of space, and the Public Share that had 880GB of space.