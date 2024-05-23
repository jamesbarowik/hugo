---
title: "Cisco Router"
date: 2024-04-17
url: /router 
image: https://www.bleepstatic.com/content/hl-images/2020/10/20/Cisco.jpg
categories:
  - Linux
  - Servers
  - Networking
  - KVM
  - Virtual Machines
draft: false
---
```Current configuration : 1583 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname Router
!
boot-start-marker
boot-end-marker
!
!
enable secret 4 56jyXs.RSLFQFX5Ebzwqm0eXTwHAtDmINcDLgnOqA16
!
no aaa new-model
memory-size iomem 5
!
ip cef
!
!
!
ip dhcp excluded-address 172.16.0.1 172.16.0.99
ip dhcp excluded-address 172.16.0.200 172.16.0.254
!
ip dhcp pool pool1
 network 172.16.0.0 255.255.0.0
 default-router 172.16.0.1
 dns-server 172.16.0.4 8.8.8.8
!
!
!
no ipv6 cef
multilink bundle-name authenticated
!
!
!
license udi pid CISCO1921/K9 sn FCZ1809C3MT
!
!
!
!
!
!
!
!
interface Embedded-Service-Engine0/0
 no ip address
 shutdown
!
interface GigabitEthernet0/0
 ip address dhcp
 ip nat outside
 ip virtual-reassembly in
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 172.16.0.1 255.255.0.0
 ip nat inside
 ip virtual-reassembly in
 duplex auto
 speed auto
!
ip forward-protocol nd
!
no ip http server
no ip http secure-server
!
ip nat pool Internet 192.168.9.20 192.168.9.20 netmask 255.255.255.0
ip nat inside source list 100 pool Internet overload
ip route 0.0.0.0 0.0.0.0 192.168.9.1
!
access-list 100 deny   ip 172.16.0.0 0.0.255.255 172.16.0.0 0.0.255.255
access-list 100 permit ip 172.16.0.0 0.0.255.255 any
!
!
!
control-plane
!
!
!
line con 0
line aux 0
line 2
 no activation-character
 no exec
 transport preferred none
 transport output pad telnet rlogin lapb-ta mop udptn v120 ssh
 stopbits 1
line vty 0 4
 password telnet
 login
 transport input telnet
!
scheduler allocate 20000 1000
!
end```