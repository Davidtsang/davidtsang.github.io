---
layout: post
title:  "Rails 如何设置中文本地化？"
categories: rails
---
#### 1 . Gemfile  
`gem "rails-i18n"`  
`bin/rake bundle install`  

#### 2 .修改 config/application.rb  
`config.i18n.default_locale = :"zh-CN"`  
