---
layout: post
title: OS Schedulers Explained In 2 Minutes
tags: operating-systems
description: Understand OS schedulers in 2 minutes!
---

-- [Atharva Bhave](https://in.linkedin.com/in/atharvabhave21)

-- [Apoorva Gokhale](https://github.com/apoorva-21)

-- [Chirag Trasikar](https://github.com/chirag16)

<img src="https://blog.oureducation.in/wp-content/uploads/2013/01/scheduling.jpg" alt="scheduling" /> 

Have you ever wondered how exactly a high level operating system like Android or Windows can run a multiple processes at the same time using only 2 or 4 hardware cores ..?

This is where schedulers come into play..!

**What is a scheduler??**

The illusion that all tasks on our device are running continuously is achieved by allowing each task to have a share of the processors' time. The process of allocating this time to each task is called “scheduling”. A scheduler is the piece of code that determines which task should be run next and how much time should be allocated for that particular task.

**How does a scheduler work??**

Based on the type of OS (i.e. if your OS is general purpose or real time) and the type of tasks (i.e. if the tasks are time triggered or event triggered) handled by the scheduler, different algorithms are used to write a scheduler program.

The typical working of scheduler is shown below:

<img src="https://www.freertos.org/implementation/suspending.gif" alt="FreeRTOS suspending" />

Referring to the numbers in the diagram above:

At (1) task 1 is executing.

At (2) the scheduler suspends (swaps out) task 1...

... and at (3) resumes task 2.

While task 2 is executing, at (4), it locks the processor peripherals for its exclusive access.

At (5) the scheduler suspends the task 2...

… and at (6) resumes the task 3.

Task 3 tries to access the peripherals but they are already locked so task 3 cannot continue hence it suspends itself at (7).

At (8), the scheduler resumes the task 1.

... etc.

The next time task 2 is executing it finishes with the processor peripherals and unlocks them at (9).

The next time task 3 is executing at (10) it can now access the processor peripherals, hence this time it executes until suspended by the scheduler.

Types of scheduler:

A scheduler is a special software which employs different strategies to decide which process to be run and also controls the removal of existing processes. Schedulers are of three types :–

1. Long term scheduler :

    Also called a job scheduler. Its primary objective is to provide a balance mix of jobs such as I/O bound (largely involving input-output operations) and processor bound(largely involving more processing than I/O). When a process changes state from NEW to READY, the job scheduler comes into play.

2. Short term scheduler:

    Also called a CPU scheduler. Its main objective is to schedule the ready processes and allocate CPU time to one of them. It is responsible for the change of ready state to running state of the processes.

3. Medium term scheduler:

    It is also called as a process swapping scheduler. When a process is suspended due to its demand for locked I/O then it can never proceed unless the I/O required is released. In this case the process is swapped to the secondary storage space to clear the main memory and to make space for other processes. So, a medium term scheduler decreases the degree of multiprogramming.

That’s all for today’s post guys, I hope you've understood what a scheduler is and how exactly it works. If you want to learn more about schedulers then you can get more information [here](https://www.tutorialspoint.com/operating_system/os_process_scheduling.htm), or you can also watch this video :

**YOUTUBE VIDEO**

<iframe width="560" height="315" src="https://www.youtube.com/embed/1fwxHAf1E88" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

_**- Atharva Bhave**_
