---
title: Arch
draft: false
tags:
  - linux
  - updateme
date:
time:
---
>**Meme**: [i use arch btw](https://www.reddit.com/r/linuxmemes/comments/9xgfxq/why_i_use_arch_btw/) :3

Cutting-edge updates, meaning it has the [latest and the most packages](https://archlinux.org/packages/) than other distros. A base-level distro that's been [[forked]] to be:
	- [endeavor os](https://endeavouros.com)
	- [garuda linux](https://garudalinux.org)
	- [cachy os](https://cachyos.org)
	- ...

---
*(note: while I've done this about 10x now, I'm rusty until I put a new OS on my T440s, so this will be updated then)*
# Steps to install
If starting from **Windows**:
+ Go to Arch, select a mirror close to you
+ Download SHA256SUM sig file next to downloaded Arch, and to check signature in terminal
	+ sha256sum *(linux os file)*
	+ check if numbers & letters are same as downloaded signature file
+ Download Rufus
+ Insert USB *(minimum 5gb)* and select it in Rufus
+ Go through steps according to your system, default options should be fine, (*unless things have changed since then*).
+ Once USB has become bootable, eject, and insert it into powered off computer.
+ Power on computer, and in the first 10 seconds press either F1, F2, F3, *(different for different computers)* to enter [[BIOS]].
+ Using up,down,left,right keys, select bootable, your USB, and exit [[BIOS]].
+ Computer will continue powering on until reaching a black screen with some input, now's the time to install Arch. *(This is Arch at its basic and can be used this way if not installing a [[DE]], in which you can download a program to search the internet through the command line, while I'm doing that for my Rasp 3B+ I doubt you will).*
	+ input into terminal: archinstall
	+ go through simple steps, don't partition drive yourself if not used to it, and select the [[DE]]/[[WM]] you want.
+ Once finished with these easy peasy steps, reboot computer and- if you're real quick, take out USB at the right moment when powered down before it restarts *(or just shutdown and take it out)*.
+ Follow a [[DE]]/[[WM]] tutorial to get things set up for [[GUI]]!