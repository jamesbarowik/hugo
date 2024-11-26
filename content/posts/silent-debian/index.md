---
title: 'Silent Debian'
date: 2024-09-02
draft: false
coverImg: "https://github.com/SilentSmeary/hugo/blob/master/images/posts/silent-debian.png?raw=true"
weight: 1
summary: "Silent Debain is a bash script that I created the script whilst learning linux to make the installation process quicker"
tags: ["linux", "debian", "automated", "bash script"]
---
## Introduction:
I had wanted to learn linux for the longest time but never really got the opportunity as in a learning situation Windows was the operating system that was used, then same for the work placement. Which ment I got really comfortable using the Windows operating system.

Linux was something that interetsted me from the first time that I had looked into it as it was different from everthing else that I'd use before. I have previously used Windows 7, 8, 8.1, 10 and am currently writing this from a Windows 11 machine. I would be daily driving linux on my Main Machine but there was some issues related to the graphics card that made it nearly impossible for that to happen

As part of College I was given the chance to be placed on a Bursary Scheme which ment that I was able to get resources purchased for me, As the only course that I did was the Digital T Level I wanted a laptop, I had browsed the market for laptops for a good couple of days before stumbling across the Lenovo ThinkPad T480s which for me was the perfect laptop, The reviews that I had read and watched stated that the battery life was amazing which ment I could work on the move and didnt have to worry about my computer running out of battery. The T480s is sold in a 14" inch variant which meant that it wasn't too big to carrry around all day and ment that it was still large enough to do daily work with no issues. The laptop has 16GB of DDR4 3200mhz RAM which was more then enough with half been soldered and half been on the board in Sodimm format it ment that I could replace or upgrade if required.

After the laptop had arrived I spent a few days checking around for the best linux distro that worked for me and did everything that I need it to do. After searching and installing various operating systems I had found that Debian 12 (Bookworm) worked the best for me as it was quick supported the KDE Plasma Desktop Environment. 

Now onto the point of the blog post.

## The actual script:
I had previously made one bash script before that was for the RPi-5 with the whole goal of that been to automate the install process of them for college, This in the meantime was for myself and any others that were intersted in using the script

I wanted to make it as quick and easy as possible that is what I decided to move to using the package manager [nala](https://gitlab.com/volian/nala) that was benchmarked to be 16x faster than normal apt-get

Firstly, I wanted to make sure that the script removed most of the default KDE programs that personally I didn't use or had alernatvies for that I had used for a long time before so felt no need to change and stop using them.

After that I made sure that the browser that I used got installed [Thorium](https://github.com/Alex313031/thorium) Aswell as Visual Studio Code, Github Desktop Client and a few other nice utility programs were installed aswell

I made sure that I installed virt-manager as in my opinon is it the best Virtual Machine manager that is on linux.

To make sure that the script didn't leave files everywhere I made sure to do all of the downloads to a temp folder called "local-downloads" this ment that the folder could be deleted everytime to reduce the size of the system and to reduce the chance of errors as there might be more than one of the same file that was downloaded.

When the first version of the script was ready I had the intent for people to use it via cloning the git repo this seemed a bit clunky and could have caused some issues for people who aren't that experienced with git cli.

After checking out other Linux Toolbox Repo's main the [ChrisTitusTech LinUtil Repo](https://github.com/christitustech/linutil) and found that it was possible to curl the setup.sh file that would mean you didnt need to download the whole git repo and then run it like that. This meant that the script could be used via one command

```bash
curl -fsSL https://raw.githubusercontent.com/SilentSmeary/silent-debian/main/setup.sh | sh
```

```bash
curl -fsSL https://raw.githubusercontent.com/SilentSmeary/silent-debian/main/setup-dev.sh | sh
```

## Other:
As part of learning linux I also found that Chris Titus had made a fully automated script for installing a good looking and useful terminal so in the README.md my repo I have also linked that with credits and given instructions on how to use this

## Link to the Repo:
[https://github.com/silentsmeary/silent-debian](https://github.com/silentsmeary/silent-debian)