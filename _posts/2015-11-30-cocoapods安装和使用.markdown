---
layout: post
title: "cocoapods安装和使用"
comments: true
share: true
tags: iOS技术
---

### 1.查看pod是否有和版本```pod --version```
### 2.国内被墙和更换源的方法,并用淘宝源安装cocoapods
<pre><code>
sudo gem update --system
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem sources -l
sudo gem install cocoapods
pod setup --verbose --no-repo-update
</code></pre>
更新完之后再确认一下cocoapods版本:```pod --version```
### 3.安装指定版本的cocoapods
例如，```sudo gem install cocoapods -v 0.34.4```
### 4.为项目建立cocoapods第三方库
```cd project目录```,
```touch Podfile```,```open -e Podfile```,按照第三方库指定的方式填入Podfile文件中，执行```pod setup --verbose --no-repo-update```安装
### 5.使用pod搜索第三方库
```pod search AFNetworking```
## 参考资料
[cocoapods安装和使用](http://blog.csdn.net/eqera/article/details/39312125);
[使用cocoapods为项目建立第三方库](http://blog.csdn.net/jymn_chen/article/details/19202397)
