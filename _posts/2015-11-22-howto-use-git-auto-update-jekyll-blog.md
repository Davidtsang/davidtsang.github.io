---
layout: post
title:  "如何利用Git自动化更新jekyll blog"
categories: git
---


在服务器上建立一个文件夹  

`mkdir gits`  

`cd gits`  

`mkdir myblog.git`  

`cd myblog.git`  

`git init --bare`  

`cd hooks`  

`vim post-receive`

编辑这个文件  

    #!/bin/bash -l
    GIT_REPO=/home/rails/gits/myblog.git
    TMP_GIT_CLONE=$HOME/tmp/myblog
    PUBLIC_WWW=$HOME/www/kejike.com/davidtsang

    git clone $GIT_REPO $TMP_GIT_CLONE
    jekyll build --source $TMP_GIT_CLONE --destination $PUBLIC_WWW
    rm -Rf $TMP_GIT_CLONE
    exit
  

`sudo chmod +x post-receive `

安装jekyll
`sudo gem install jekyll`


本地jekyll blog git增加remote  
USER@YOURDOMAIN.com:~/gits/myblog.git  

push remote



