---
layout: post
title:  "Git部署Rails Web APP"
categories: git
---
####server side
  cd ~
  mkdir gits
  mkdir gits/testapp.git
  mkdir apps
  mkdir apps/testapp
  cd gits/testapp.git
  git init --bare

.Git/hooks/post-receive

    #!/bin/sh
    GIT_WORK_TREE=/home/rails/apps/nsjenglish git checkout -f

参考：
<https://gist.github.com/yortz/1047083>
