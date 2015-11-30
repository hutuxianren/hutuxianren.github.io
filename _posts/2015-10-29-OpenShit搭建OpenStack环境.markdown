---
layout: post
title: "OpenShit搭建OpenStack环境"
comments: true
share: true
tags: OpenStack笔记
---
OpenShit命令介绍
<pre><code>
./openshit.sh <--all|service_name> start|stop|restart
</code></pre>
可对各个(或者全部)OpenStack组件进行启动，停止，重启操作。

<pre><code>
./openshit.sh <--all|service_name> install|uninstall|download
</code></pre>
可对OpenStack组件进行安装，卸载，下载操作。

```./openshit.sh <--all|service_name> config```
可以配置组件各项服务。

```./openshit.sh <--all|service_name> clean```可以清除服务的数据库，若服务出问题了可以直接清掉数据库然后重新config

***
###安装步骤
1.  ```  git  clone https://github.com/windworst/openshit.git``` 
2. 修改配置文件setting.conf.里面有很多密码:数据库密码,服务密码.默认的可以更改,不改也没什么.改变网络配置.配置文件内IP值都设置称自己的IP, 网卡设置成自己的网卡(默认为eth0).<h3>两个地方需要改ip地址，其余的只是索引.</h3>
3. 配置文件修改完成后开始安装
     ```cd openshit```

      ```./openshit.sh --all install.```
     这个命令会 问你是否需要配置软件源, 第一次使用openshit请选择y, 所以命令可以这样写:
      ```echo y | ./openshit.sh --all install```
  注:安装失败时重新执行此命令，选择no
4. 一段时间后安装完成,请输入
       ```./openshit.sh --all config```
       会根据setting.conf的值修改各个组件的配置文件以及数据库配置.(如有问题，应该是安装开始的时候输了root密码，这时进setting.conf文件改mysql密码为刚刚输入的密码)

5. 完成后运行```source admin-env.sh```; ```nova service-list``` 查看服务状态若都为up安装成功
       在浏览器内打开 http://ip地址/horizon即可看到Openstack管理界面输入密码可登陆
dashboard登录名和密码采用keystone认证，在setting.conf中有显示。
一般为admin/admin888,登入成功即表示成功。
