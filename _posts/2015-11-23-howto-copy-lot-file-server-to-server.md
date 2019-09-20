---
layout: post
title:  "如何在服务器之间拷贝文件？"
categories: server
---

###
方法一：  

`scp /file/to/send username@remote:/where/to/put`

方法二：  
`tar c some/dir | gzip - |  ssh host2 tar xz`
