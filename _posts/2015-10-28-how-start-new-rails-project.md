---
layout: post
title:  "如何新建一个RAILS WEBAPP项目"
categories: rails
---

#### 新建一个Rails APP 

在.gitignore文件中加入

    # Ignore other unneeded files.
    database.yml
    doc/
    *.swp
    *~
    .project
    .DS_Store
    .idea
    .secret

`git init`  
`git add .`  
`git commit -m"init" `  

#### Gemfile中加入一些常用的Gems  

    gem 'devise'
    gem 'bootstrap-sass', '~> 3.3.5'
    gem 'font-awesome-sass'
    gem 'rest-client', '~> 1.8'    

#### 设置Devise  

`rails generate devise:install`

修改routes.rb  
`root 'static_pages#home'`

run:  
`rails generate devise User`  

`bin/rake db:migrate`  

config/environments/development.rb  
增加一行:  
`config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }`  


`rails g controller static_pages home about`

测试下：  
`rails s`  
一切正常。



