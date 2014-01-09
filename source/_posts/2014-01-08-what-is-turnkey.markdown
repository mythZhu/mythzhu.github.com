---
layout: post
title: "What is TurnKey"
date: 2014-01-08 21:37
comments: true
categories: 
---

------

*Turnkey Linux* is a virtual appliance library that integrates and polishes the
very best open source software into ready to use solutions. Each virtual appliance
is optimized for ease of use and can be deployed in just a few minutes on bare
metal, a virtual machine and in the cloud.
<!--more-->

------

## Background ##

The following background knowledge could help you understand 'what is TurnKey linux'.
If you have been similiar with them, you could skip this section.

### JeOS ###

[JeOS](http://en.wikipedia.org/wiki/Just_enough_operating_system) is the abbreviation
(pronounced "juice") for Just Enough Operating System as it applies to a software
appliances and embedded operating systems.

Typically, a JeOS consists of the following:

- OS core (kernel, drives, etc.)
- OS minimum maintenance tools
- Minimum user space tools
- Packages repository (DVD or network based)

### Software appliance ###

A [software appliance](http://en.wikipedia.org/wiki/Software_appliance) is a software
application that might be combined with JeOS for it to run optimally on industry
standard hardware (typically a server) or in a virtual machine.

Software appliances have several benefits over traditional software applications
that are installed on top of an operating system:

- Simplified deployment (dependency, compatibility, conflict)
- Improved isolation (security, crash)

There two main types of software appliances:

- Live CD appliance
- Virtual appliance

### Virtual appliance ###

A [virtual appliance](http://http://en.wikipedia.org/wiki/Virtual_appliance) is
a virtual machine image designed to run on a virtualization platform (e.g.,
VirtualBox, Xen, VMware Workstation, Parallels Workstation).

Virtual appliances are a subset of the broader class of software appliances.
Installation of a software appliance on a virtual machine and packaging that into
an image creates a virtual appliance.

------

## Benefits ##

- Save time and money with 100+ ready-to-use solutions

- It just works

- Backup and migration

- Secure and easy to maintain

- 100% Open Source

- Based on Debian 7.2 ("Wheezy")

- Easy to use

- Lightweight (starting from 150MB

- Assured integrity

------

## Installation ##

Installing to a VirtualBox is one of the fastest and easiest ways to get up and
running with TurnKey Linux. The installation process is the same for all appliances.
We'll be installing [LAPP](http://www.turnkeylinux.org/lapp) as an example.

### Install VirtualBox ###

If you haven't done so already, download and install [VirtualBox](http://www.virtualbox.org).

### Download image ###

[VM optimized images](http://www.turnkeylinux.org/docs/builds#vm) and
[Generic ISO image](http://www.turnkeylinux.org/docs/builds#iso) work well with
VirtualBox. We will choose default VM build and use that.

### Create new VM ###

Unzip the default VM build and lauch the VM creation wizard by clicking the *New*
button in VirtualBox:

- OS Type: Linux / Ubuntu
- Memory:  at least 256 MB
- Virtual Hard Disk: use an existing hard disk

### Configurate VM ###

After you've created the new VM, you'll need to tweak its configuration:

- Settings > System > Processor > Enable PAE/NX
- Settings > Network > Adapter 1 > Attach to: bridged

Now boot your virtual appliance for the first time.

------

## Development ##

[TKLDev](http://www.turnkeylinux.org/tkldev) is the mother of all TurnKey appliances.
It's used to give birth to all other appliances, including new versions of itself.
It includes a self-contained appliance development toolchain and build system that
can be used by appliance hackers to fabricate any existing or new TurnKey appliance
from source.

With TKLDev, building an appliance from scratch is as easy as grabbing the source
and running make.

### Install TKLDev ###

Like any other TurnKey appliance, TKLDev is available for download in multiple 
build formats from the TurnKey Linux website.

TKLDev doesn't support cross-architecture builds. That means building an amd64
type appliance image requires an amd64 build of TKLDev.

Shellinabox (as well as Webmin) is installed but disabled by default so as not
to conflict with appliance builds. You should connect via an SSH client.

### Setup TKLDev ###

By convention, the source code for an appliance is placed within tkldev in
/turnkey/fab/products (e.g., /turnkey/fab/products/core, /turnkey/fab/products/wordpress,
etc.).

Before you build your first appliance, you will need to download 3 prerequisite
build dependencies and place them into their appropriate paths within the TKLDev
filesystem:

- `/turnkey/fab/bootstraps`: contains minimal bootstrap filesystems.
- `/turnkey/fab/cdroots`: contains the cdroot template for the built ISO.
- `/turnkey/fab/common`: contains source code shared amongst all TurnKey appliances.

Click [here](https://github.com/turnkeylinux-apps/tkldev/blob/master/docs/setup.rst)
for more details for this.

### Build appliance ###

Now that everything is in place, clone the source code of TurnKey Core, and perform
the build:

```
cd /turnkey/fab/products
git-clone https://github.com/turnkeylinux-apps/core.git
cd core
make
```

The above will create build/product.iso which you should copy to your host system
for testing in a VM.

Finally, perform cleanup:

```
deck -D build/root.tmp
make clean
```

