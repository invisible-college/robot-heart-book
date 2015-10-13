# Vagrant and VirtualBox

Vagrant is a tool for provisioning and controlling VirtualBox images and instances. This section should probably be in the Appendix somewhere, for the ultimately curious on how to create their own VirtualBox images. As always, this is not meant to be a definitive guide, just the way I did it, and it worked for me, once upon a time.

Prerequisites
=============

To do this tutorial, you'll need the latest [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed to actually create and run the virtual Linux images. I'm using 5.0.6.

```
> % virtualbox --help
Oracle VM VirtualBox Manager 5.0.6
(C) 2005-2015 Oracle Corporation
All rights reserved.
```

You'll also need [Vagrant](http://www.vagrantup.com/downloads) installed. I'm using 1.7.4 for Mac OSX.
```
$ vagrant --version
Vagrant 1.7.4
```

Creating the Base Box
---------------------

First, I create a directory to hold my Vagrant files (which are not the same as the VirtualBox image, which is much larger) and I create a fresh Git repo. I pretty much version everything these days privately, even if I never push them to GitHub or expose them publicly. Especially for teaching purposes, having a private, local git repo lets you keep track of what changes over time, especially when it's made by an automated tool or GUI like Android Studio.

```
ppham@Pauls-Air [04:08:49] [~/src]
-> % mkdir robot-heart
ppham@Pauls-Air [04:09:09] [~/src]
-> % cd robot-heart
ppham@Pauls-Air [04:09:13] [~/src/robot-heart]
-> % git init
Initialized empty Git repository in /Users/ppham/src/robot-heart/.git/
ppham@Pauls-Air [04:10:16] [~/src/robot-heart] [master]
-> %
```

Initialize an empty Vagrant file in the current directory using HashiCorp's base Ubuntu LTS image. I'm running a 64-bit machine. If you still have a 32-bit machine, use the image `precise32` below instead.

```
-> % vagrant init hashicorp/precise64
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

Troubleshooting
===============

Outdated Vagrant
----------------

If you get the following message, likely you have upgrade VirtualBox to a version which is not tested or usable with your Vagrant version.

```
~/src/robot-heart ‹›  ‹master*› $ vagrant up
No usable default provider could be found for your system.

Vagrant relies on interactions with 3rd party systems, known as
"providers", to provide Vagrant with resources to run development
environments. Examples are VirtualBox, VMware, Hyper-V.

The easiest solution to this message is to install VirtualBox, which
is available for free on all major platforms.

If you believe you already have a provider available, make sure it
is properly installed and configured. You can see more details about
why a particular provider isn't working by forcing usage with
`vagrant up --provider=PROVIDER`, which should give you a more specific
error message for that particular provider.
```

In this case, I was using Vagrant 1.7.2 with VirtualBox 5.0.6.

References
----------

* [Official Vagrant documentation for creating a new base box](https://docs.vagrantup.com/v2/getting-started/index.html)
* [New Relic tutorial]()