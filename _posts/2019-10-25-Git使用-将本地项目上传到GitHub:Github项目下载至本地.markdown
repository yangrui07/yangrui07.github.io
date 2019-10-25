---
layout: post
title:  "Git使用-本地项目上传到GitHub/Github项目下载至本地"
date:   2019-10-25 15:46:00 +0800
categories: git
---
操作平台：macOS Mojave v10.14.3
<h1>1、在GitHub 上创建新仓库</h1>
<ul>
    <li>登录后，主页点击"New repository"</li>
    <li>输入仓库名<br><strong>注意⚠️ 仓库名应该与本地项目名一致</strong></li>
    <li>点击"Create repository" 即可生成仓库项目</li>
</ul>
<h1>2、配置SSH</h1>
<p>打开Terminal，输入命令：</p>
{% highlight ruby %}
 $ cd ~/.ssh
 {% highlight ruby %}
 $ ssh-keygen
 {% endhighlight %}
 <p>会在 `.ssh`文件中生成 `id_rsa.pub`，将此文件内容（ssh key）添加到Github中，Github主页-账号-设置-SSH-New SSH Key</p>
<h1>3、本地代码上传至Github</h1>
 {% highlight ruby %}
$ git add .
$ git commit -am"update info"
$git push origin master
 {% endhighlight %}
<h1>4、Github项目下载到本地</h1>
 {% highlight ruby %}
$ cd /Documments/Github/myblog
$ git clone git@github.com:yangrui07/yangrui07.github.io.git
 {% endhighlight %}
 