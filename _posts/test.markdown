---
layout: post
title: "murder she bittorrented"
date: 2013-10-18 14:20:30
categories: 
---

There's a rather well known project called [murder][murder] that was written originally by some folks at Twitter. It uses Bittorent to push files to a large amount of production servers. There's a [video][murdervid] explaining it with that oh-so-twitter baby blue color everywhere that you should totally watch if you want more info.

The one downside is that its pretty beastly to implement if you're not already using Capistrano. Our particular need was to integrate Murder into another on-demand system that has to push some files around to worker bees. The files were pretty large, so bittorrent was the natural "speed 'em up" perscription.

There's a great little project called [Herd][herd] that simplifies Murder to a simple python script. Which I have to say, is pretty perfect. After making a few little patches to bubble up errors and provide better help text (committed back to source of course), it's much nicer to use. It's a replacement for Murder that just uses the same design and logic. 

After installing eventlet and argparse modules (probably already there for you), you have to do 2 things: 1) Make sure you can [ssh without passwords][ssh] to every server, and 2) put those lists of servers (one per line) into a file. The examples all call it hosts.dat, and looks like this:

{% highlight console %}
$ cat hosts.dat
10.0.0.8
10.0.0.9
somebox.localdomain.tld
anotherbox
{% endhighlight %}

Then you just run this command: :

	$ $ ./herd.py -h
	usage: herd.py [-h] [--retry RETRY] [--port PORT] [--remote-path REMOTE_PATH]
	               [--data-file DATA_FILE] [--log-dir LOG_DIR]
        	       local-file remote-file hosts
	
	positional arguments:
	  local-file            Local file to upload
	  remote-file           Remote file destination
	  hosts                 File containing list of hosts

	optional arguments:
	  -h, --help            show this help message and exit
	  --retry RETRY         Number of times to retry in case of failure. Use -1 to
        	                make it retry forever (not recommended)
	  --port PORT           Port number to run the tracker on
	  --remote-path REMOTE_PATH
                	        Temporary path to store uploads
	  --data-file DATA_FILE
                        	Temporary file to store for bittornado.
	  --log-dir LOG_DIR     Path to the directory for murder logs
	$ ./herd.py local-file.tar.gz /tmp/remote-file.tar.gz ./hosts.dat

When we were testing this at scale, we found that even using bittorent, pushing 2TB files to a few hundred nodes caused some interesting network saturation problems. That caused the bittorent client to bail and the files wouldn't get pushed. We did find though, that just retrying a few times was all that was needed. So I tossed in a `--retry` flag to accomplish just that. If it detects a failure from bittorent (like connection failure, md5sum mismatches, etc), it will try X more times before dieing forever and sending the errors to your `--log-dir` (one file per host). That makes error remediation much easier at large scale.

So yeah, I can now say we are sucessfully using Herd to transfer petabytes of data a day, and it was much easier to drop in than embracing the full blown Murder/Capistrano stack.


[murder]: https://github.com/lg/murder
[murdervid]: http://vimeo.com/11280885
[herd]: https://github.com/russss/Herd
[ssh]: http://sshkeychain.sourceforge.net/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html
