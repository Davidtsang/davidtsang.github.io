---
layout: post
title:  "GIT一般工作流程"
categories: git
---

git一般工作流程  
###1. 创建分支 

`$ git checkout -b modify-README`

查看下branch状态：  
`git branch`

然后编码
###2. commit分支
 `git commit -a -m "Improve the README file"`

###3. 切换回主干
`git checkout master`

### 4. 合并分支
`git merge modify-README`

### 5. 删除分支
如果分支不需要了，删除  
`git branch -d modify-README`
