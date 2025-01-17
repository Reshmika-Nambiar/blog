---
layout: post
title: What is FIFO and LIFO??!
tags: operating-systems
description: Understand FIFO and LIFO.
---

-- [Rohit Bhaskar](https://github.com/rohitbhaskar)

-- [Chirag Trasikar](https://github.com/chirag16)

![](/assets/posts/what-is-fifo-and-lifo/fifolifo.jpg)

A very important (yet easy to understand) topic in computer engineering. LIFO and FIFO refer to methods of storage of data in memory stacks. A memory stack is nothing but a set of memory locations in a block of memory. (Computer science students might have made use of the concept of stack memory quite often).

The stack memory is nothing but a fixed set of memory locations that is reserved for storage when the code runs. This memory is mainly used when functions are called.

There are 2 operations that go along with any stack memory, and those are the Push and Pull operations. The Push instruction is used to load data onto the stack, and the Pull instruction is used to take data from the stack. Based on the method of storage and accessing of data, the stack can be classified into 2 types.
1. LIFO
2. FIFO

In LIFO type memory, the data that is stored last on the stack is removed 1st. i.e It the data to be stored stacks on top of each other.  
In FIFO type memory the data that is stored 1st is removed 1st. It is like accessing the stack from below.

Both the methods are used in different situations based on the system requirement. An example of LIFO is the stack memory that is used in 8085 and 8086 micro-processors. FIFO, on the other hand is widely used in accounting tools and software.

Hope you understood!! Take a look [here](http://www.diffen.com/difference/FIFO_vs_LIFO) to read more about it!
