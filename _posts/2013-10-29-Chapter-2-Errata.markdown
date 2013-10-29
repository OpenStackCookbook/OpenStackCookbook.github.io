---
layout: post
title: "Chapter 2 Errata"
date: 2013-10-29 14:13:49
categories: errata
---

While every effort went into ensuring you got a top quality cookbook for OpenStack, inevitablly things slipped through. That in turn leads us to these Errata sections. We will have one of these per chapter, in which we list: the section the error is in, the error itself, and what is should be, or how to fix it.

- **Section:** Installing OpenStack Image Service - There's more...   
**Issue:** PPA resources.   
**Fix:** No longer needed for Havana.

- **Section:** Managing images with OpenStack Image Service - Getting ready   
**Issue:** "export OS_AUTH_URL=http://172.16.0.1:5000"   
**Fix:** "export OS_AUTH_URL=http://172.16.0.200:5000"

- **Section:** Sharing images among tenants - Getting ready   
**Issue:** "export OS_AUTH_URL=http://172.16.0.1:5000"   
**Fix:** "export OS_AUTH_URL=http://172.16.0.200:5000"

- **Section:** Viewing shared images - Getting ready   
**Issue:** "export OS_AUTH_URL=http://172.16.0.1:5000"   
**Fix:** "export OS_AUTH_URL=http://172.16.0.200:5000"

To submit issues, you can file them as issues on our github page [here](https://github.com/OpenStackCookbook/OpenStackCookbook.github.io).
