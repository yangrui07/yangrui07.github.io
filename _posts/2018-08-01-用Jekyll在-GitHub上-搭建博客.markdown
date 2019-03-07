---
layout: post
title:  "用Jekyll在 GitHub上 搭建博客"
date:   2018-08-02 16:46:00 +0800
categories: jekyll update
---
搭建平台：macOS Mojave v10.14.3
<h1>1、安装Ruby</h1>
<p>Mac本身有Ruby，但我们用 homebrew (Homebrew是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件)再装一个 ruby, 这样 local 归 local, system 归 system.</p>
 Install homebrew
 $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
Install Ruby
$ brew install ruby
Install jekyll
$ gem install jekyll bundler

本地创建Jekyll site
$ bundle exec Jekyll serve

Fixed the issue:
<p>安装完Ruby后我们需要修改其路径，不然系统会使用默认的。可以使用 which ruby查看目前使用的是哪个一个ruby的bin命令</p>
{% highlight ruby %}
$ echo 'export PATH=/usr/local/Cellar/ruby/1.9.3-p0/bin:$PATH' >> ~/.bash_profile $ export PATH=/usr/local/Cellar/ruby/1.9.3-p0/bin:$PATH
{% endhighlight %}
接下来执行如下命令：
{% highlight ruby %}
$ which ruby
{% endhighlight %}
输出结果是 /usr/local/Cellar/ruby/1.9.3-p0/bin/ruby
<h2>安装Jekyll 遇到的问题</h2>
<p>Error:
	jekyll 3.4.0 | Error:  Operation not supported on socket @ rb_sysopen - /Users/ruiy/Library/Application Support/Google/Chrome/App Shim Socket</p>
这个问题是因为没有进入到Jekyll目录(ruiy/blog)执行jekyll serve





[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
