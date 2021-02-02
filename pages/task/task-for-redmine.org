# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for installing redmine
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: myclass
#+LATEX_CLASS_OPTIONS: [a4paper]
#+ATTR_LATEX: width=0.38\textwidth wrap placement={r}{0.4\textwidth}
#+ATTR_LATEX: :float multicolumn
#+REVEAL_TRANS: None
#+REVEAL_THEME: Black
#+TAGS: @work(w) @home(h) @road(r) laptop(l) pc(p) { @read : @read_book @read_ebook }
#+ATTR_ORG: :width 30
#+ATTR_HTML: width="100px"
#+EXPORT_SELECT_TAGS: export
#+EXPORT_EXCLUDE_TAGS: noexport
#+STARTUP: fold

* tasks for installing redmine in Windows Server 2016 Datacenter
** [2020]
*** [2020-04]
**** [2020-04-21 二]
***** Operating System: Windows server 2016 DataCenter (64 bit, 2GB RAM)
***** download packages[3/8]
      - [X] MySQL 8.0
      - [X] rubyinstaller-devkit-2.6.6-1-x64.exe
      - [X] redmine-4.1.1.zip (GPL v2)
***** install as Administrator [11/11]
      - [X] install MySQL and add bin/ to PATH
      - [X] install ruby to C:/Ruby27-x64 and add to PATH
      - [X] unpack redmine to a directory, e.g. C:/redmine/redmine-4.1.1
      - [X] Create an empty database and accompanying user - MySQL-Feng_db2048
#+BEGIN_SRC sql
CREATE DATABASE redmine CHARACTER SET utf8mb4;
CREATE USER 'redmine'@'localhost' IDENTIFIED BY 'Redmine_password-2020';
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost';
#+END_SRC
      - [X] Database connection configuration
        Copy config/database.yml.example to config/database.yml; edit:
  production:
  adapter: mysql2
  database: redmine
  host: localhost
  username: redmine
  password: "Redmine_password-2020"
      - [X] Authentication plugin ‘caching_sha2_password’ cannot be loaded
#+BEGIN_SRC sql
use mysql;
select user,plugin from user where user='redmine';
ALTER USER 'redmine'@'localhost' IDENTIFIED BY 'Redmine_password-2020' PASSWORD EXPIRE NEVER;
ALTER USER 'redmine'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Redmine_password-2020';
ALTER USER 'redmine'@'%' IDENTIFIED WITH mysql_native_password BY 'Redmine_password-2020';
FLUSH PRIVILEGES;
#+END_SRC
      - [X] Dependencies installation - in shell - cd C:/redmine/redmine-4.1.1
#+BEGIN_SRC shell
gem sources
# https://rubygems.org/
# clean sources
gem sources -c
# update sources
gem sources -u
# 安装bundle
gem install bundler

# 这一条命令可能会报错，查看报错信息，按提示解决
#bundle install --without development test rmagick
bundle config set without 'development test rmagick'
bundle install

# 生成数据库会话
bundle exec rake generate_secret_token

# 创建数据库中需要的表
#bundle exec rake db:migrate RAILS_ENV="production"
set RAILS_ENV=production
gem uninstall eventmachine
gem install eventmachine --platform=ruby
bundle exec rake db:migrate

set REDMINE_LANG=zh
bundle exec rake redmine:load_default_data

# 启动服务
ruby bin/rails server -e production

# 安装thin服务器
gem install thin
# 修改redmine目录下Gemfile文件，添加一行代码
#gem "thin", :group => :production
group :production do
  gem "thin"
end
# 启动服务
ruby bin/rails server thin -e production

# 修改端口
ruby bin/rails server thin -e production -p 3001
#+END_SRC
      - [X] create a file called: "Gemfile.local" in C:/redmine/redmine-3.6.6
#+BEGIN_SRC shell
#It will be loaded automatically when running bundle install.
# Gemfile.local
gem "thin"
#+END_SRC
      - [X] Test the installation - webrick - not for production
#+BEGIN_SRC shell
bundle exec rails server webrick -e production
#+END_SRC
            browser to http://localhost:3000/.
            You should now see the application welcome page.
            login: admin
            password: admin change to Redmine4SparkSource
      - [X] Configuration
            Redmine settings are defined in a file named config/configuration.yml.
            If you need to override default application settings, simply copy
            config/configuration.yml.example to config/configuration.yml and
            edit the new file; the file is well commented by itself, so you
            should have a look at it.
      - [X] Email Configuration: see for 163
        [[https://www.redmine.org/projects/redmine/wiki/EmailConfiguration][email configuration]]
        要使用163邮箱的smtp服务得专门开通才行。开通服务在:
        设置->邮箱设置->客户端设置->设置客户端授权密码
$ vim apps/redmine/htdocs/config/configuration.yml
# default configuration options for all environments
default:
  # Outgoing emails configuration
  # See the examples below and the Rails guide for more configuration options:
  # http://guides.rubyonrails.org/action_mailer_basics.html#action-mailer-configuration
  email_delivery:
    delivery_method: :async_smtp
    smtp_settings:
      tls: false
      address: smtp.163.com
      port: 25
      domain: smtp.163.com
      authentication: :login
      enable_starttls_auto: true
      user_name: 你的邮箱@163.com
      password: 客户端授权密码(不是邮箱登录密码)
...
# 下面还有很多邮箱的配置，不用管
...
# specific configuration options for production environment
# that overrides the default ones
production:
    delivery_method: :async_smtp
    smtp_settings:
      tls: false
      address: smtp.163.com
      port: 25
      domain: smtp.163.com
      authentication: :login
      enable_starttls_auto: true
      user_name: 你的邮箱@163.com
      password: 客户端授权密码(不是邮箱登录密码)
【保存并退出】
注意：是用"客户端授权密码",否则在邮件发送会提示未授权的错误。

重启redmine的服务
$ ./ctlscript.sh restart

检查redmine的邮件发送功能：
在 "管理->配置->一般"标签下：
将“主机名称”改成 ：
IP/redmine
【保存】

在 "管理->配置->邮件通知"标签下：
"邮件发送人地址"改成:
你的邮箱@163.com
再点右下角的"发送测试邮件"按键即可。
**** [2020-04-25 六]
    - minimize windows cmd.exe window with auto start [0/0]
    - [X] minimize
#+BEGIN_SRC shell
@echo off
%1 (start /min cmd.exe /c %0 :&exit)
REM your command here

pause
#+END_SRC
    - [X] autostart
通过组策略设置脚本随服务器启动
开始->运行->gpedit.msc->计算机配置->Windows设置->脚本（启动/关机）
添加启动脚本就可以了
