+++
title = 'Fix /dev/null (apply to other char devices too)'
date = 2024-02-25T14:56:16+09:00
draft = false
hideToc = true
tags = ["linux"]
categories = ["linux"]
series = ""
+++

Today I was playing with my gentoo linux, maybe did some wild stuff, and the shell complains about invalid /dev, I took a look at it and found out /dev/null becomes a regular file, instead of a character device file. Here is a solid way to fix it, by creating the device file:

```shell
# as root 
rm /dev/null
# create new node
mknod /dev/null c 1 3
chmod 666 /dev/null
```

That's it, plain and simple.
