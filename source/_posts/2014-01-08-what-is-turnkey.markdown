---
layout: post
title: "What is TurnKey"
date: 2014-01-08 21:37
comments: true
categories: 
---

------

Turnkey Linux is a virtual appliance library that integrates and polishes the very
best open source software into ready to use solutions. Each virtual appliance is
optimized for ease of use and can be deployed in just a few minutes on bare metal,
a virtual machine and in the cloud.
<!--more-->

-----

## JeOS ##

[JeOS][2] is the abbreviation (pronounced "juice") for Just Enough Operating System as
it applies to a software appliances and embedded operating systems.

Typically, a JeOS consists of the following:

- JeOS media (OS core {kernel, virtual drives, login})
- OS minimum maintenance tools
- Minimum user space tools
- Packages repository (DVD or network based)

-----

## Software appliance ##

A [software appliance][3] is a software application that might be combined with JeOS
for it to run optimally on industry standard hardware (typically a server) or in a
virtual machine.

### Benefits ###

Software appliances have several benefits over traditional software applications that
are installed on top of an operating system:

- *Simplified deployment*: A software appliance encapsulates an application's dependencies
  in a pre-integrated, self-contained unit. This can dramatically simplify software
  deployment by freeing users from having to worry about resolving potentially complex
  OS compatibility issues, library dependencies or undesirable interactions with other
  applications. This is known as a "toaster".

- *Improved isolation*: Software appliances are typically used to run applications
  in isolation from one another. If the security of an appliance is compromised, or
  if the appliance crashes, other isolated appliances will not be affected.

### Types ###

- Live CD appliance
- Virtual appliance

-----

## Virtual appliance ##

A [virtual appliance][4] is a virtual machine image designed to run on a virtualization
platform (e.g., VirtualBox, Xen, VMware Workstation, Parallels Workstation).

Virtual appliances are a subset of the broader class of software appliances. Installation
of a software appliance on a virtual machine and packaging that into an image creates a
virtual appliance.

-----

## Why to use ##

- *Save time and money with 100+ ready-to-use solutions*: discover and leverage the
  best free open source software. Deploy in minutes on bare metal, virtual machines,
  or in the cloud.

- *It just works*: designed for ease of use, built and pre-tested by a community of
  experts.

- *Backup and migration*: smart software saves changes to files, databases and package
  management to encrypted storage which servers can be automatically restored from.

- *Secure and easy to maintain*: auto-updated daily with latest security patches.

- *100% Open Source*: free from expensive and restrictive proprietary licensing. Easy
  to customize and extend to build new appliances from the closest existing starting
  point.

- *Based on Debian 7.2 ("Wheezy")*: with automatic security updates for over 39,000
  packages. The TurnKey Linux virtual appliance library is licensed under the same
  terms as Debian. In other words, you are free to download, use, redistribute and
  modify a virtual appliance for any purpose.

- *Easy to use*: includes a web management interface, web shell, and simple configuration
  console (screenshots).

- *Lightweight (starting from 150MB)*: each virtual appliance is carefully built from
  the ground up with the minimum components needed to serve its role with maximum
  efficiency and security.

- *Assured integrity*: solutions are built from verfiably unmodified Debian binaries,
  except for a few custom components for which full source code is available. Releases
  are cryptographically signed.

-----

## How to install ##

Installing to a VirtualBox is one of the fastest and easiest ways to get up and running
with TurnKey Linux. The installation process is the same for all appliances. We'll be
installing [TurnKey Joomla][5] as an example.

### Install VirtualBox ###

If you haven't done so already, download and install [VirtualBox][6].

### Download image ###

[VM optimized images][7] and [Generic ISO image][8] work well with VirtualBox. We will
choose default VM build and use that.

### Create new VM ###

Unzip the default VM build and lauch the VM creation wizard by clicking the *New* button
in VirtualBox:

- OS Type: Linux / Ubuntu
- Memory:  at least 256 MB
- Virtual Hard Disk: use an existing hard disk

### Configurate VM ###

After you've created the new VM, you'll need to tweak its configuration:

- Settings > System > Processor > Enable PAE/NX
- Settings > Network > Adapter 1 > Attach to: bridged

Now boot your virtual appliance for the first time.


[1]: <http://www.turnkeylinux.org> "Turnkey Linux"
[2]: <http://en.wikipedia.org/wiki/Just_enough_operating_system> "JeOS"
[3]: <http://en.wikipedia.org/wiki/Software_appliance> "Software appliance"
[4]: <http://http://en.wikipedia.org/wiki/Virtual_appliance> "Virtual appliance"
[5]: <http://www.turnkeylinux.org/joomla> "Joomla"
[6]: <http://www.virtualbox.org> "VirtualBox"
[7]: <http://www.turnkeylinux.org/docs/builds#vm> "TurnKey vm images"
[8]: <http://www.turnkeylinux.org/docs/builds#iso> "TurnKey iso images"
