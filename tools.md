# Tools

Code is your craft. When you take pride in your craft, you can spend a lot of time geeking out about tools, talking shop with other coders. Many an hour can be whiled away discussing the relative merits of your favorite text editor.

Think of your computer as your electronics workshop, and of individual software components inside of it as the resistors, soldering iron, and oscilloscope for building new creations.

Android Software Development Kit
================================

A software development kit is all the files and tools you'll need to start writing an app using a particular platform or framework. In this case, the Android SDK is the official distribution from Google, and needs to be downloaded before you can do anything else.

https://developer.android.com/sdk/installing/index.html

If you'd like to download the standalone version, which you can use on the command-line or with any integrated development environment (IDE) like Eclipse or Android Studio, download the standalone version.

These packages, up to API Version 23 (Android 6.0 ) can be found in this tutorial's VirtualBox image.


Amazon Web Services (AWS)
=========================

Amazon offering their internal web services on a pay-as-you-go basis to external clients is one of the biggest changes to the startup and software landscape. When my friends started Jamglue in 2008.

Amazon Web Services, hereafter forever referred to as AWS, is an indispensable collection of services which can be used together or separately to support your Android app. Note that there is nothing specifically in AWS that mentions Android. However, mobile apps and web apps share a lot of needs in common, so the hacker mindset can easily see ways of repurposing web services for apps, which after all, are just another consumer of data over the internet. And AWS doesn't care if you are building web apps or mobile apps: they just see you as another potential customer.

The best part of AWS is it is easy to try for free. Their Free Tier includes Elastic Compute Cloud (EC2) for hosting and provisioning fully-functional instances of Linux machines (sometimes on bare metal), Simple Storage Service (S3) for remote and flexible file storage, Internet of Things (IoT) for connecting embedded devices, and many others. These services have a generous allowance in the Free Tier, and once you exceed these limits, congratulations! That means you've grown your service to the point that you have many customers, hopefully paying you lots of money, so now you can afford to graduate to a paid tier or even some other service entirely if AWS can't meet your needs.

You can sign up for an AWS Free Tier account here:
http://aws.amazon.com/free/

Elastic Computer Cloud (EC2)
----------------------------

The most basic service AWS provides is a virtual computer running in the cloud, a home for you to run tasks. The major advantage of using EC2 is that it can be preconfigured for you, and it's always running. So you don't have to worry about the particular versions of software packages or operating systems running on your laptop, which may change over time and break your ability to compile and run your Android apps. That's what makes EC2 particularly useful for teaching, especially when combined with VirtualBox and Vagrant.

Simple Storage Service
----------------------

Often you need a place to keep persistent storage on the web that you can access in a uniform, public way. You can't keep files like this in Heroku, since they got stomped over every time you re-deploy, and in general, Heroku limits the amount of filesystem storage you can use. It's also good engineering practice to keep your data, especially when there's a lot of it (potentially gigabytes) separate from your code, which is much smaller (.

Enter S3, AWS's storage service. You could store things in DropBox, but you'll probably run up against the free 14 GB or so limit pretty soon, especially if you're collaborating with more than a few people or have Camera Sync turned on.

We'll be using S3 for a variety of purposes in this book, including distributing the  main VirtualBox image.

Virtualization
==============

```
Any problem in computer science can be solved with another level of indirection.
---Donald Knuth
```

In the before days, running your own website meant keeping a big, loud, hot desktop computer under your desk, possibly next to your bed. You had to keep this computer on all the time. If it ever went off, your website was "down" and people couldn't browse your cat pictures or your comprehensive list of links to movie trivia. (This problem has since been solved by services like Interplanetary Filesystem IPFS). (TODO Find out how to do blockquotes in Markdown).
You were responsible for patching this machine and keeping it up-to-date with security advisories, being constantly on alert against script kiddies in Eastern Europe, Korea, Brazil (the traditionally great sources of 14-year-olds with too much time on their hands).

Virtualization partially solves this problem by introducing another layer of indirection. Like the Great Knuth teaches us, virtualization inserts another layer of indirection. Instead of running an operating system and packages directly on a computer, namely your own computer, you can run a simulation of a computer on top of another computer. This simulation can be stoppped, started, re-provisioned, updated, all remotely and through software itself. You can then easily charge people for this service on your own physical computer, which can now swap in and out of these virtual simulations as easily as you would put on a jacket for going out.

Virtualization software includes VMWare (paid commercial software) and VirtualBox (a free and open source contribution from Oracle) for home users and personal laptops. We'll concentrate on VirtualBox in this tutorial. This software is what allows you to run a Linux operating system on your Mac laptop, a Windows operating system on your Linux desktop, or any other combination of operating systems you can imagine.

VirtualBox
==========

You can download the latest version of VirtualBox from this website.
https://www.virtualbox.org/wiki/Downloads
We will use Version 5.0.6.

TODO Have a script which detects when version number changes.

Vagrant
=======

Vagrant is a tool for provisioning and controlling VirtualBox images and instances. Provisioning is the process of creating a virtual operating system container, allocating space for it, and installing packages.

Normally downloading all the files and configuring them for an Android development environment would take you many hours, probably over several days. As a new Android developer, this was time well spent for me to really learn at a low-level all the different steps and technical debugging skills. However, for you, I'd like you to save this time. One of the philosophical tenets in this book is to save you time when possible, to guide you in learning the best techniques and tools at the current moment to get up and running with the wild and woolly animal that is Android app development. But at the same time, we'd like to leave it open for you to continue exploring areas that interest you, and which you can take as a tangent.

You are starting now as a newbie, a neophyte, Android programmer, much like I was when I started writing this book. However, we're going to help accelerate your growth as fast as humanly possible. We are hackers at heart, and one of the greatest joys in life is hacking our own learning process so that it can take a fraction of the time you would have spent learning on your own.

By the end of this book, you'll be able to make your own tools, and improve on the ones we've given you. The primary tool right now is a VirtualBox image which contains the exact Android development environment that you  need to run the examples in this book without a hitch.

If like me, you have difficulty focusing, than going on a guided tour (especially with a teacher or programming coach) will help you get the most out of this book.

For this tutorial, we've created a snapshot which you can download here:

[TODO Learn how to share virtualbox images via vagrant, possibly also distributed using ipfs].

To start with, let's provision a simple image for an Ubuntu Linux box as a base

Ansible
-------

Consider.It uses Ansible for provisioning. I should read more about it, and why I should use it instead of just creating a single authoritative image and distributing that everywhere.
