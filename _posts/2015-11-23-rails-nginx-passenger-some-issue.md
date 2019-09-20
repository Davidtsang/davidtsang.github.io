---
layout: post
title:  "Rails passenger 部署在一些问题"
categories: rails
---
找不到js runtime:  

Gemfile  
`gem 'therubyracer', platforms: :ruby`


Bundle install无效  

`bundle install --deployment`.  

`bundle install --no-deployment`.
