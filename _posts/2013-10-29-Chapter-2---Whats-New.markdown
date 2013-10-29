---
layout: post
title: "Chapter 2 - What's New: Starting OpenStack Image Service"
date: 2013-10-29 13:25:06
categories: havana
---

In this chapter, the following sections have changed for the Havana release of OpenStack:

- Installing OpenStack Image Service
- New Section: Configure Glance Known Image Stores

#Installing OpenStack Image Service#
Only a subset of this section changes. Specifically, the "Using an alternative release" section changes. At this time, there is no need to use the PPA resources for Havana as they will no longer work.

#New Section: Configure Glance Known Image Stores#
> Note:
>
> Ideally, you would add this section before or just after the "Configuring OpenStack Image Service with OpenStack Identity Service" section of the book.

As an image store, OpenStack Glance allows you to configure a number of backend systems such as: OpenStack Swift, S3, HTTP, RBD, and others. 

##Gettting Ready##
Ensure you are logged in to the OpenStack Controller. To log into the Controller host we created with Vagrant, use the following command:
	vagrant ssh controller

##How to do it...##
To configure the known image stores for OpenStack Glance, issue the following command:

	sudo sed -i 's/^#known_stores.*/known_stores = glance.store.filesystem.Store,\
	       glance.store.http.Store,\
	       glance.store.rbd.Store,\
	       glance.store.s3.Store,\
	       glance.store.swift.Store/' /etc/glance/glance-api.conf

#Summary#
This post covered a small change in chapter 2 of "The OpenStack Cloud Computing Cookbook, 2nd edition" as well as added a section on configuring Glance.