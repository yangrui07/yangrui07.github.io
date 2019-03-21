---
layout: post
title:  "用Jekyll在 GitHub上 搭建博客"
date:   2018-08-02 16:46:00 +0800
categories: jekyll update
---
搭建平台：macOS Mojave v10.14.3
<h1>1、安装Ruby</h1>
<p>Mac本身有Ruby，但我们使用 homebrew (Homebrew是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件)再装一个 ruby, 这样 local 归 local, system 归 system.</p>
首先安装Homebrew
{% highlight ruby %}
 $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" {% endhighlight %}
然后安装 Ruby
 {% highlight ruby %}
 $ brew install ruby
 {% endhighlight %}
<h1>2、安装Jekyll</h1>
 {% highlight ruby %}
$ gem install jekyll bundler
 {% endhighlight %}
<h1>3、本地创建Jekyll文件</h1>
 {% highlight ruby %}
$ bundle exec Jekyll serve
 {% endhighlight %}
 <h1>4、提交到Github上</h1>
 {% highlight ruby %}
$ git pull origin master
$ git add .
$ git commit -am"update info"
$ git push origin master
 {% endhighlight %}
<h4 style="color:red">遇到的问题以及解决办法</h4>
<p>安装完Ruby后系统会有两个Ruby，为了解决冲突，因此我们需要修改其路径。</p>

可以使用如下命令来检查当前使用的ruby
{% highlight ruby %}
$ which ruby
{% endhighlight %}

修改并重置其目录，即可。
{% highlight ruby %}
$ echo 'export PATH=/usr/local/Cellar/ruby/1.9.3-p0/bin:$PATH' >> ~/.bash_profile $ export PATH=/usr/local/Cellar/ruby/1.9.3-p0/bin:$PATH
{% endhighlight %}
<p>若遇到一下报错，是因为没有进入到Jekyll目录执行jekyll serve</p>
{% highlight ruby %}
jekyll 3.4.0 | Error:  Operation not supported on socket @ rb_sysopen - /Users/ruiy/Library/Application Support/Google/Chrome/App Shim Socket
{% endhighlight %}
<p>至此使用Jekyll构建博客已经完成！</p>
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/