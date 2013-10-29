---
layout: post
title: "Chapter 1 Errata"
date: 2013-10-29 13:57:15
categories: errata
---

While every effort went into ensuring you got a top quality cookbook for OpenStack, inevitablly things slipped through. That in turn leads us to these Errata sections. We will have one of these per chapter, in which we list: the section the error is in, the error itself, and what is should be, or how to fix it.

- **Section:** Creating Tennants   
**Issue:** "export ENDPOINT=1172.16.172.200"   
**Fix:** "export ENDPOINT=172.16.0.200"

- **Section:** Creating the service tenant and service users   
**Issue:** "export ENDPOINT=1172.16.0.200"   
**Fix:** "export ENDPOINT=172.16.0.200"

To submit issues, you can file them as issues on our github page [here](https://github.com/OpenStackCookbook/OpenStackCookbook.github.io).