---
layout: post
title: "ubuntu 14.04中安装 ruby on rails 环境"
date: 2015-07-13
---
##下载必要的的软件##

我用的是ubuntu14.04，Vmware虚拟机

先修改更新源和替换软件源，选择mirrors.163.com，打开终端，输入命令：

sudo gedit /etc/apt/sources.list

先备份一下，在把
```
deb http://mirrors.163.com/ubuntu/ raring main universe restricted multiverse
deb-src http://mirrors.163.com/ubuntu/ raring main universe restricted multiverse
deb http://mirrors.163.com/ubuntu/ raring-security universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ raring-security universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ raring-updates universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ raring-proposed universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ raring-proposed universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ raring-backports universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ raring-backports universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ raring-updates universe main multiverse restricted
```
然后更新：

sudo get-apt update

安装可能使用的库

```
$ sudo apt-get install -y build-essential openssl curl libcurl3-dev libreadline6 libreadline6-dev git zlib1g zlib1g-dev libssl-dev libyaml-dev libxml2-dev libxslt-dev autoconf automake libtool imagemagick libmagickwand-dev libpcre3-dev libsqlite3-dev libmysql-ruby libmysqlclient-dev
```
安装RVM

```
$ curl -L https://get.rvm.io | bash -s stable  
//若提示找不到公钥，执行下边语句
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
//然后，重新执行，安装完rvm之后，需配置终端，以便下次打开终端能直接只用rvm。更改终端配置方法：参见https://rvm.io/integration/gnome-terminal
$ curl -L get.rvm.io | bash -s stable
//至此，rvm安装完成，下边我们手动为终端配置rvm环境，否则以后在终端中可能每次都要手动加载rvm环境
//更改终端配置方法：工具栏--编辑--配置文件首选项--标题和命令--命令--选中“以登录shell方式运行命令”
//然后，我们手动加载rvm环境，将服务器资源改为淘宝的
///////$ source ~/.rvm/scripts/rvm 官方的加载rvm环境命令，我们就不执行了
//临时加载rvm环境，参考：https://rvm.io/integration/gnome-terminal
$ source ~/.bashrc
$ source ~/.bash_profile
//更改rvm源服务器资源信息，毕竟国外的经常被墙掉，还有就是国内的速度快。若不设置，下面可能出现各种问题，如出现服务器积极拒绝（被墙），或者下载速度慢
$ sed -i -e 's/ftp\.ruby-lang\.org\/pub\/ruby/ruby\.taobao\.org\/mirrors\/ruby/g' ~/.rvm/config/db
//请保存你的工作，然后重启ubuntu系统
```

检验一下
```$ rvm -v  ```
3. 安装Ruby
要先执行一下，不然下面的流程跑不动。
```
$ rvm install ruby 
//安装完，看一下安装的版本
$ ruby -v
//通过下面操作，我们把这个作为ruby默认版本，若是你机子上有多个版本的话，参考：https://ruby-china.org/wiki/install_ruby_guide步骤3
```

配置gem的源，国内必须国外可选

```
$ gem source -r https://rubygems.org/  
$ gem source -a http://ruby.taobao.org  
```
下面代码安装rails
```
$ gem install rails
//若报错相关信息nokogiri-1.6.5.gem，缺少这个包，或者这个包有问题安装不上，执行下边命令手动安装nokogiri
$ gem install nokogiri -v=1.6.5
//如果安装nokogiri报错，需要依赖包 libxslt libxml2，那我们就先装这俩依赖包
$ sudo apt-get install libxslt libxml2
//装完依赖包后，继续安装nokogiri-1.6.5.gem
$ gem install nokogiri -v=1.6.5
//安装完nokogiri，我们就可以继续rails的安装步骤了
$ gem install rails
//安装完后，查看rails版本
$ rails -versions
//这时，应该是最新的4.2.0　
```

最后检查工具是否齐全
```
ruby -v
rails -v
sqlite3 --version
```