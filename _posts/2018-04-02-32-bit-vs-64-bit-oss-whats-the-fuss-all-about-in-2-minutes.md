---
layout: post
title: 32-bit vs. 64-bit OSs : What's the Fuss All About ? : In 2 Minutes
tags: operating-systems
description: Understand the difference between 32-bit and 64-bit OSs.
---

-- [Bansi Derashri](https://in.linkedin.com/in/bansii)

-- [Apoorva Gokhale](https://github.com/apoorva-21)

-- [Chirag Trasikar](https://github.com/chirag16)

<img src="https://steemitimages.com/0x0/https://www.beatlabacademy.com/wp-content/uploads/2015/07/32-vs-64.png" alt="32-bit 64-bit" /> 

Are you thinking of extending your laptop's RAM because it runs at the speed of a turtle? Wait before you do that! because you might end up wasting money without getting improved results, except the lighter wallet.

We'll just quickly go through basic terms (techies can GOTO the next paragraph directly). Computers only know Binary when it comes to computing, i.e they know 1's and 0's, and these are called bits. In 1 bit computing, you get two possible values; 2 bit computing ,you get 4 possible values; 32 bit computing, you get (2 to the 32nd power) worth 4,294,967,296 values(4 gigabytes); 64-bit (or 2 to the 64th power) is worth 18,446,744,073,709,551,616 values(16 exabytes). Damn,that's a lot of bits and we can clearly make out **how a chip with more bits 'can' have its computing power more than doubled.**

Now, about an Operating System (OS) ,it works as **an interface between computer hardware and an end user** like you. How well your computer utilize system hardware largely depends on OS.

Let's say you and a toddler are given a corn to eat. Obviously because you have stronger teeth you will be able to savour it's taste on a rainy day and the poor toddler will probably just try hard to eat and fail multiple times before giving up. I want to make a point here,your system chipset is corn in this case and teeth is your OS.

Let's have a look at how computer system is made.

<img src="https://i.stack.imgur.com/LPAbZ.jpg" alt="computer system" />

It is clear from the image that to run a 64 bit application we require a 64 bit OS and 64 bit chip set. Now basically 64 bit architecture and 32 bit architecture have difference in size of their registers.  A register is a small amount of storage where the CPU keeps whatever data it needs to access quickly for optimal computer performance.Coming to OSes,the main difference between them is in the amount of RAM they utilize.(Random Access Memory, or RAM (pronounced as ramm), is the physical hardware inside a computer that temporarily stores data, serving as the computer's "working" memory.) 32 bit OS utilize 4GB of RAM theoretically while 64 bit OS can utilize 17.2 billion GBs of RAM(This number is too big and as of now we don't have efficient hardware to support this theoretical statement 😉)(*note*:Windows 64-bit Home editions are still limited to 16 GB of RAM for licensing reasons, but the Professional and Ultimate versions can use up to 192 GB of RAM).

So, a system having 64bit architecture will have a greater computing power but for it's proper utilization we require a 64 bit version of OS,we can't install a 32 bit version of OS and expect it to address larger amount of RAM(few smarties might have got the reason behind the first statement of this blog).

**The biggest drawback of 32 bit OSs is the restriction in usage of RAM**, also a part of RAM is utilized by video cards and other such applications further reducing the size of RAM that your OS actually accesses. 64 bit OS comes to the rescue here!  
A system with 64 bit OS is more efficient , uses more memory and **can allot more memory to individual applications**(engineers who use huge softwares like autoCAD know the problems faced while using such applications 😉). This also means that your video cards and other devices will not be stealing usable memory space from the operating system.

Hope you have understood why there is no dearth of computers with 64 bit today.

If you are still curious to know which system you are using follow the instructions [here](https://support.microsoft.com/en-in/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64).

_**-Bansi Derashri**_
