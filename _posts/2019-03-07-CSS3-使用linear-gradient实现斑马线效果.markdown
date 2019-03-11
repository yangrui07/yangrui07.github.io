---
layout: post
title:  "使用linear-gradient实现斑马线效果"
date:   2019-03-07 17:46:00 +0800
categories: jekyll update
---
<h2>前言</h2>
<p>起初是在CSS开发者大会上知道了魔法哥，他会用纯CSS实现一些形状、简单的Icon。这样就不会再引用图片造成请求资源的浪费，于是也对CSS充满了好奇。在后来了解到这本书：《CSS Secrets》更加对渴望学习更多的CSS知识。使用linear-gradient实现斑马线效果，是在微信中看了一篇Web前端开发的推送，内容包含如何css、js的相关基础知识，文中提到怎么用CSS实现斑马条纹背景，于是脑海中跳出的第一个想法就是使用伪元素:before/:after，然后尝试用后并没有实现预想的效果，于是搜到了网上大神使用linear-gradient即可实现。经过实践后，决定记录下来以便日后使用查看。</p>

初始化的渐变效果：
{% highlight ruby %}
background:linear-gradient(#fb3, #58a);
{% endhighlight %}

如果将两种颜色的过渡点调的更近一些：
{% highlight ruby %}
background:linear-gradient(#fb3 20%, #58a 80%);
{% endhighlight %}

容器顶部20%都是#fb3，底部20%都是#58a，所以实际上渐变的部分只占有了


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
