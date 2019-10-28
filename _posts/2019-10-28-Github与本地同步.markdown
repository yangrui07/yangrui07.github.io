---
layout: post
title:  "Git使用-Github项目下载至本地-本地项目上传到GitHub.markdown"
date:   2019-10-25 16:46:00 +0800
categories: jekyll update
---
操作平台：macOS Mojave v10.14.3
<h1>1、配置SSH</h1>
<p>打开Terminal，输入命令：</p>
{% highlight ruby %}
 $ cd ~/.ssh
 $ ssh-keygen
 {% endhighlight %}
 <p>会在 `.ssh`文件中生成 `id_rsa.pub`，将此文件内容（ssh key）添加到Github中，Github主页-账号-设置-SSH-New SSH Key</p>
<h1>2、将Github项目下载到本地</h1>
 {% highlight ruby %}
$ cd /Documments/Github/myblog
$ git clone git@github.com:yangrui07/yangrui07.github.io.git
 {% endhighlight %}
<h1>3、将本地代码上传至Github</h1>
 {% highlight ruby %}
$ cd /Documments/Github/myblog
$ git add .
$ git commit -am"update info"
$ git push origin master
 {% endhighlight %}
 <p>此时执行Git命令需要在.git父级目录下执行</p>

 