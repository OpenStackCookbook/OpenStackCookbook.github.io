---
layout: post
title: "Chapter 1 - What's New"
date: 2013-10-29 10:13:00
categories: havana 
---

# Chapter 1 - OpenStack Keystone Identity Service #

In this chapter, the following sections have changed for the Havana release of OpenStack:
* Creating a sandbox environment 
* Configuring Ubuntu Cloud Archive

> **Note:**
> The intention of these chapters is to provide you with only the information and steps required to preform the corresponding sections of the book for the Havana release of OpenStack.

## Creating a sandbox environment using VirtualBox and Vagrant ##
To support the recipes in this book and provide a hands on environment where you can work with the recipes we discuss.

> **Tip:**
> At the time of this update, the versions of softare are as follows:
> * Vagrant: 1.3.5
> * VirtualBox: 4.2.18

> **Tip:**
> It is assumed your computer will have at least 8GB of ram as well as the Intel VT-X or AMD-V support.

1. Install VirtualBox from (http://www.virtualbox.org/)
2. Install Vagrant from (http://vagrantup.com/)
3. Once installed, we define our environment using a file called a *Vagrantfile*. To do this, run the following code:

	mkdir ~/cookbook
	cd ~/cookbook
	vim Vagrantfile

4. 