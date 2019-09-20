---
layout: post
title:  "如何在Ubuntu上安装RVM、Ruby on rials、Passgenger与Nginx？"
categories: rails
---

###准备工作

如果你是root登陆的用户，你需要创建一个非root用户来管理这些东西，这是最好的选择。

`adduser rails`

然后rails加入sudo组

`gpasswd -a rails sudo`
----------
首先
`apt-get update`

安装一些依赖：

`sudo apt-get install build-essential libssl-dev libyaml-dev libreadline-dev openssl curl git-core zlib1g-dev bison libxml2-dev libxslt1-dev libcurl4-openssl-dev nodejs libsqlite3-dev sqlite3`

安装RUBY 2.1.7

`mkdir ~/ruby`

`cd ~/ruby`

`wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.7.tar.gz`

`tar -xzf ruby-2.1.7.tar.gz`

`cd ~/ruby-2.1.7`

`sudo ./configure`

`sudo make`

`sudo make install`

`ruby -v` 显示 `ruby 2.1.7p400 (2015-08-18 revision 51632) [i686-linux]` 安装成功

`rm -rf ~/ruby`

`sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 561F9B9CAC40B2F7`

`sudo nano /etc/apt/sources.list.d/passenger.list`

插入一行 `deb https://oss-binaries.phusionpassenger.com/apt/passenger trusty main`

`sudo chown root: /etc/apt/sources.list.d/passenger.list`

`sudo chmod 600 /etc/apt/sources.list.d/passenger.list`

`sudo apt-get update`

`sudo apt-get install nginx-extras passenger`

`sudo rm /usr/bin/ruby`
`sudo ln -s /usr/local/bin/ruby /usr/bin/ruby`

`sudo nano /etc/nginx/nginx.conf`

    # passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    # passenger_ruby /usr/bin/ruby;

CHANGE TO :

    passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    passenger_ruby /usr/local/bin/ruby;


参考网址： <https://www.digitalocean.com/community/tutorials/how-to-deploy-a-rails-app-with-passenger-and-nginx-on-ubuntu-14-04>

####install MYSQL
`sudo apt-get install mysql-server mysql-client libmysqlclient-dev`

####install PostegerSQL  

`sudo apt-get install postgresql postgresql-contrib`
 
`sudo -i -u postgres`

`psql`

你可以为postgres设置一个密码,例如postgres  
`\password postgres`  

返回  

`exit`

继续配置NGINX  

`sudo nano /etc/nginx/sites-available/default`  

找到这两行:  

    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

注释掉:  

    # listen 80 default_server;
    # listen [::]:80 default_server ipv6only=on;


`sudo nano /etc/nginx/sites-available/testapp`  

Add the following server block. The settings are explained below.  

    server {
      listen 80 default_server;
      server_name www.mydomain.com;
      passenger_enabled on;
      passenger_app_env development;
      root /home/rails/testapp/public;
    }

创建符号链接:  

`sudo ln -s /etc/nginx/sites-available/testapp /etc/nginx/sites-enabled/testapp`  

`sudo nginx -s reload`  

####安装一些必要的GEM
    gem install rdoc
    gem install bundler
    gem install rake 

##### 一些问题
有时候会出现 passenger_native_support.so successfully loaded. 或者找不到curl wget之类的错误
nginx.conf文件头部加一句
`env PATH;`  

下面的不适用。
----

<del>####STEP1 :安装RVM

<del>`gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`

 <del>然后
 <del>`\curl -sSL https://get.rvm.io | bash -s stable`

<del>`source /etc/profile.d/rvm.sh`

<del>`rvm requirements`

<del>####STEP2: 安装RUBY AND RAILS

<del>`rvm install 2.0.0`

<del>`rvm use 2.0.0 --default`

<del>`gem install rails`

<del>####STEP3: 安装PASSENGER
<del>`gem install passenger `

<del>`apt-get install libcurl4-openssl-dev`

<del>Opps！提示虚拟内存不够，按照提示修改下。（你机器内存大无需关注下面这段代码）

<del>    sudo dd if=/dev/zero of=/swap bs=1M count=1024
<del>    sudo mkswap /swap
<del>    sudo swapon /swap

<del>####SETP4: 安装Nginx
<del>`rvmsudo passenger-install-nginx-module`

<del>####INSTALL MYSQL
<del>`sudo apt-get install mysql-server mysql-client libmysqlclient-dev`

