---
layout: post
title: "birth of my blog"
date: 2014-10-27 15:24:52 +0800
comments: true
categories: 
---

##准备工作##
申请一个github帐号:hongxin1988

建一个名为hongxin1988.github.io的repo
##安装msysgit##
到[这里](http://msysgit.github.io/)下载msysgit并安装

配置ssh
	```
		ssh-keygen -C github-account-email -t rsa
	```
##安装octopress##
Octopress2.0需要ruby1.9.3,我的机子是windows，可以通过RubyInstaller来安装.到[这里](http://rubyinstaller.org/downloads/)下载[Ruby1.9.3-p545](http://dl.bintray.com/oneclick/rubyinstaller/ruby-1.9.3-p545-i386-mingw32.7z?direct)以及[DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe](https://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe) 安装即可。也就是下面的1、2两步
<!--more-->
安装ruby，比较简单，直接双击即可。

安装DevKit.先解压。然后进入目录，如下所示：

	cd C:\DevKit<br>
	ruby dk.rb init<br>
	ruby dk.rb install<br>
	gem install rdiscount --platform=ruby

安装octopress

	cd d:\github
	git clone git://github.com/imathis/octopress.git octopress
	cd octopress
	ruby --version # Should report Ruby 1.9.3
rubygems.org在国内下载的速度会很慢，先切换到国内的镜像源，找到octopress下的Gemfile，修改第一行为： source "http://ruby.taobao.org"

	gem install bundler
	bundle install
	rake install # 安装默认的octopress主题

部署到github
 
	rake setup_github_pages # 首先将octopress与github关联起来,根据提示完成即可
	rake generate # 这个命令主要是根据source目录的内容，编译生成JeKyll所需要的静态文件，存放到public目录下
	rake deploy # 该命令首先清空\_deploy目录，然后将public目录整个拷贝过来，然后commit到github。_deploy 目录对应着master分支。

source 目录下保存了所有的markdown源文件，是博客的原始数据，以及一些模板文件。将Octopress 备份到source分支

	git add .
	git commit -m "initial source file"
	git push origin source

访问 http://hongxin1988.github.io 就可以看到一个初始化的博客主页了。接下来写第一篇博客，按照惯例，从Hello World 开始。

##来一发 Hello World##

	rake new_post["hello world"] # 这个命令会在octopress\source_posts目录下建一个markdown文件。按照markdown的格式往这个文件里写博客的内容即可。
	rake generate** # 生成最终的博客文件
	rake deploy # 将public目录下的内容拷贝到\_deploy目录下，并把内容commit且push到master分支。
访问博客主页，http://hongxin1988.github.io 即可。好兴奋  ^_^

做好备份。
	
	git add .
	git commit -m "add a blog named hello world"
	git push origin source

##博客简单配置##
###导航条###
文字改成中文，并加上“我的微博”以及"关于我"。
###添加多说评论###
看[这里](http://havee.me/internet/2013-02/add-duoshuo-commemt-system-into-octopress.html)就ok啦。
###添加百度统计###
注册百度统计帐号，将代码添加到下面这个文件即可：

	source/_includes/after_footer.html


##参考资料##
 - [octopress官方主页](http://octopress.org/docs/deploying/github/)
 - [GitHub Pages 使用github + Octopress 搭建免费博客](http://linglong117.blog.163.com/blog/static/27714547201332895056387/)
 - [利用Octopress搭建一个Github博客](http://beyondvincent.com/blog/2013/08/03/108-creating-a-github-blog-using-octopress/)
 - [GotGitHub](http://www.worldhello.net/gotgithub/03-project-hosting/050-homepage.html)
 - [为 Octopress 添加多说评论系统](http://havee.me/internet/2013-02/add-duoshuo-commemt-system-into-octopress.html)

##感谢##
 [biaobiaoqi](http://biaobiaoqi.me) 和 [heapstacks](http://heapstacks.com) 的指导让我在最短的时间内搭建好我的博客。 
