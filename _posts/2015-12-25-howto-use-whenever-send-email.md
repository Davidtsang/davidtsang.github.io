---
layout: post
title:  "如何在使用Whenever定时发送邮件"
categories: rails
---

<https://github.com/javan/whenever>

### install  
`gem 'whenever', :require => false`

### init
`wheneverize .`    
This will create an initial config/schedule.rb file for you.  
#### config/schedule.rb  

    env :PATH, ENV['PATH']
    set :output, "log/cron_log.log"
    #set :environment,  "development"
    every 1.day , :at => '4:30 am' do
      rake send_daily_notice_email
    end
  
make a rake task:
### lib/tasks/send_daily_notice_email.rake

    desc 'send daily notice email'
    task send_daily_notice_email: :environment do
      # ... set options if any
      User.send_daily_notice_email
    end
  
#### 使cronjob生效
`whenever -w`
