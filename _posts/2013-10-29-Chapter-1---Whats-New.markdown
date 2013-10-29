---
layout: post
title: "Chapter 1 - What's New"
date: 2013-10-29 10:13:00
categories: havana 
---

# Chapter 1 - OpenStack Keystone Identity Service #

In this chapter, the following sections have changed for the Havana release of OpenStack:

- Configuring Ubuntu Cloud Archive

The intention of these chapters is to provide you with only the information and steps required to preform the corresponding sections of the book for the Havana release of OpenStack.

## Configuring Ubuntu Cloud Archive ##

Ubuntu 12.04 LTS, the release used in the OpenStack Cookbook provides a number of repositories for installing OpenStack. The standard repositoy is based on OpenStack Essex. The second edition of the book as published, shows you how to use the Ubuntu Cloud Archive to provide Grizzly. With the Havana release of OpenStack, the Ubuntu Cloud Archive also needs to be updated.


> Note:
>
> These recipies assume you are building by hand rather than using the completed scripts in the OpenStack Cookbook GitHub. If you are using the scripts from GitHub, this work has been done for you.

### Getting Started ###
Ensure you are logged into the server that will become home to Keystone. In our example this is the 'controller'. This server needs to be accessible to the remainder of your OpenStack hosts.

### How to do it...###
Log into the controller node and execute the following steps:
1. To add the Ubuntu Cloud Archive, we add the repository as follows:
	# Grizzly Goodness
	sudo apt-get -y install ubuntu-cloud-keyring
	echo "deb http://ubuntu-cloud.archive.canonical.com/ubuntu precise-updates/grizzly main" | sudo tee -a /etc/apt/sources.list.d/grizzly.list
	echo "deb  http://ubuntu-cloud.archive.canonical.com/ubuntu precise-proposed/grizzly main" | sudo tee -a /etc/apt/sources.list.d/grizzly.list
2. Before we can use this repository, we need to ensure we have the Ubuntu Cloud Archive Key. We add this key as follows:
	sudo apt-get update
	sudo apt-get -y install ubuntu-cloud-keyring

###Summary###
This post covers the changes needed to ensure you are using the Havana release of OpenStack with the OpenStack Cookbook.