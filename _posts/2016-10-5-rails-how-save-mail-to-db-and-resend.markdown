---
layout: post
title:  "Rails如何存储email到数据库，然后取出发送？"
categories: rails
---

### save to db

	mail = UserMailer.welcome_email(@user)   
	mail.to_s    
#save the string to you table.

### exprot form db  

    mail = Mail.new(mail_string)

    ActionMailer::Base.wrap_delivery_behavior(mail)

    mail.deliver
