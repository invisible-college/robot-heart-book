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

Start up the image with Vagrant. If this is the first time you've run `vagrant up`, it will download the image from the Vagrant cloud which will take a few minutes depending on your internet connection speed. Make sure you are on a fat pipe for this part!

```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'hashicorp/precise64' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
==> default: Loading metadata for box 'hashicorp/precise64'
    default: URL: https://atlas.hashicorp.com/hashicorp/precise64
==> default: Adding box 'hashicorp/precise64' (v1.1.0) for provider: virtualbox
    default: Downloading: https://vagrantcloud.com/hashicorp/boxes/precise64/versions/1.1.0/providers/virtualbox.box
```
When you are done, downloading, you'll see a lot of other [startup messages] which are shown in the appendix.

You'll notice there are some error messages about the Guest Additions to VirtualBox which are necessary for, among other things, mounting shared folders. That's how you'll get the Android SDK files you'll need, especially if you downloaded them elsewhere. Don't worry about the error messages about X Windows, we won't be using the graphical interface until later.

Bringing up the VirtualBox image in this way is a dry run to trigger installation of the Guest Additions.

[TODO: Add screenshots for adding a Mounted Shared Folder, but we don't need them now]

We will often use our VirtualBox image from the command-line.
If you start up the VirtualBox graphical interface, you will see

While

Note that this base image of Ubuntu uses an insecure key, so that anyone can at least log into this machine once. Vagrant will immediately generate your own keypair stored locally on your own machine, and insert this key into the Ubuntu image.

```
    default: SSH address: 127.0.0.1:2200
    default: SSH username: vagrant
    default: SSH auth method: private key
```

The way you'll connect to the box is by using the `vagrant ssh`.



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

Appendix
========

Full Startup Output from `vagrant up`
-------------------------------------

```
    default: Downloading: https://vagrantcloud.com/hashicorp/boxes/precise64/versions/1.1.0/providers/virtualbox.box
==> default: Successfully added box 'hashicorp/precise64' (v1.1.0) for 'virtualbox'!
==> default: Importing base box 'hashicorp/precise64'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'hashicorp/precise64' is up to date...
==> default: Setting the name of the VM: robot-heart_default_1444779261246_75140
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
GuestAdditions versions on your host (5.0.6) and guest (4.2.0) do not match.
stdin: is not a tty
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  fakeroot linux-headers-3.2.0-23 make patch
Suggested packages:
  make-doc diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot linux-headers-3.2.0-23 linux-headers-3.2.0-23-generic make
  patch
0 upgraded, 6 newly installed, 0 to remove and 66 not upgraded.
Need to get 12.7 MB of archives.
After this operation, 68.5 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main make amd64 3.81-8.1ubuntu1 [118 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main patch amd64 2.6.1-3 [80.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main fakeroot amd64 1.18.2-1 [87.2 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main linux-headers-3.2.0-23 all 3.2.0-23.36 [11.4 MB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main linux-headers-3.2.0-23-generic amd64 3.2.0-23.36 [947 kB]
dpkg-preconfigure: unable to re-open stdin: No such file or directory
Fetched 12.7 MB in 5s (2,351 kB/s)
Selecting previously unselected package make.
(Reading database ... 51095 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.1ubuntu1_amd64.deb) ...
Selecting previously unselected package patch.
Unpacking patch (from .../patch_2.6.1-3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23.
Unpacking linux-headers-3.2.0-23 (from .../linux-headers-3.2.0-23_3.2.0-23.36_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23-generic.
Unpacking linux-headers-3.2.0-23-generic (from .../linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.1ubuntu1) ...
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up linux-headers-3.2.0-23 (3.2.0-23.36) ...
Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Copy iso file /Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso into the box /tmp/VBoxGuestAdditions.iso
stdin: is not a tty
mount: warning: /mnt seems to be mounted read-only.
Installing Virtualbox Guest Additions 5.0.6 - guest version is 4.2.0
stdin: is not a tty
Verifying archive integrity... All good.
Uncompressing VirtualBox 5.0.6 Guest Additions for Linux............
VirtualBox Guest Additions installer
Removing installed version 4.2.0 of VirtualBox Guest Additions...
Copying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Could not find the X.Org or XFree86 Window System, skipping.
An error occurred during installation of VirtualBox Guest Additions 5.0.6. Some functionality may not work as intended.
In most cases it is OK that the "Window System drivers" installation failed.
stdin: is not a tty
Restarting VM to apply changes...
==> default: Attempting graceful shutdown of VM...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => /Users/ppham/src/robot-heart
```


References
----------

* [Official Vagrant documentation for creating a new base box](https://docs.vagrantup.com/v2/getting-started/index.html)
* [Sitepoint tutorial for building and sharing a VirtualBox](http://www.sitepoint.com/create-share-vagrant-base-box/)