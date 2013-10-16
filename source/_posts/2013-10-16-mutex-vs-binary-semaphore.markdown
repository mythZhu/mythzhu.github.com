---
layout: post
title: "Mutex vs. Binary Semaphore"
date: 2013-10-16 09:53
comments: true
categories: 
---
------

Mutices and semaphores are among the most basic tools in multithreaded programming. 
However few people know what is the difference between them.
<!--more-->

------

### Mutex Is a Subset of Semaphore ###

A semaphore can be a Mutex but a Mutex can never be semaphore. This simply means 
that a binary semaphore can be used as Mutex, but a Mutex can never exhibit the 
functionality of semaphore.

### Mutex Could Be Acquired More Than Once ###

Both semaphores and Mutices are non­recursive in nature, while Mutices could but 
not recommanded be implemented as recursive ones.

### Mutex is More Responsible than Semaphore ###

No one owns semaphores, whereas Mutex are owned and the owner is held responsible 
for them. This is an important distinction from a debugging perspective. In the 
case of Mutex, the thread that owns the Mutex is responsible for freeing it. 
However, in the case of semaphores, this condition is not required. Any other 
thread can signal to free the semaphore.

### Different Purpose ###

A Mutex, by definition, is used to serialize accesses to a section of re­entrant 
code that cannot be executed concurrently by more than one thread. A semaphore, 
by definition, restricts the number of simultaneous users of a shared resource up 
to a maximum number.

### Different Scope ###

Another difference that would matter to developers is that semaphores are system 
wide and remain in the form of files on the filesystem, unless otherwise cleaned 
up. Mutex are process­wide and get cleaned up automatically when a process exits.

The nature of semaphores makes it possible to use them in synchronizing related 
and unrelated process, as well as between threads. Mutex can be used only in 
synchronizing between threads and at most between related processes (the pthread 
implementation of the latest kernel comes with a feature that allows Mutex to be 
used between related process).

### Mutex is Light than Semaphore ###

According to the kernel documentation, Mutices are lighter than semaphores. What 
this means is that a program with semaphore usage has a higher memory footprint 
when compared to a program having Mutex.

### Mutex is Simpler than Semaphore ###

From a usage perspective, Mutex has simpler semantics when compared to semaphores.

