---
layout: post
title:  "使用linear-gradient实现斑马线效果"
date:   2019-03-07 17:46:00 +0800
categories: jekyll update
---
<h2>前言</h2>
<p>起初是在CSS开发者大会上知道了魔法哥，他会用纯CSS实现一些形状、简单的Icon。这样就不会再引用图片造成请求资源的浪费，于是对CSS充满了好奇。在后来了解到这本书：《CSS Secrets》更加对渴望学习更多的CSS知识。</p>
<p>使用linear-gradient实现斑马线效果，是在微信中看了一篇Web前端开发的推送，内容包含CSS、JS的相关基础知识，文中提到怎么用CSS实现斑马条纹背景，于是脑海中跳出的第一个想法就是使用伪元素:before/:after，尝试后并没有实现预想的效果，于是搜到了网上大神使用linear-gradient即可实现。经过实践后，决定记录下来以便日后使用查看。</p>

初始化的渐变效果：
{% highlight ruby %}
background:linear-gradient(#fb3, #58a);
{% endhighlight %}
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 0 0;width: 300px;height: 198px'></div>
如果将两种颜色的过渡点调的更近一些：
{% highlight ruby %}
background:linear-gradient(#fb3 20%, #58a 80%);
{% endhighlight %}
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 0 397px;width: 300px;height: 198px'></div>
容器顶部20%都是#fb3，底部20%都是#58a，所以实际上渐变的部分只占有了60%，那么渐变的部分就会更小了。如果颜色过渡点相同会发生什么呢？
{% highlight ruby %}
background:linear-gradient(#fb3 50%, #58a 50%);
{% endhighlight %}
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 0 590px;width: 300px;height: 188px'></div>
如果多个颜色过渡点位置相同，那么就会在两个颜色之间生成一个无限小的过渡。实际效果就是，一个颜色不再会流畅地过渡到下一个颜色，而是会突然变成下一个颜色。

<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 300px 0;width: 298px;height: 194px'></div>
因为渐变本质上就是<em>background-image</em>，所以我们可以使用<em>background-size</em>来调整大小：
{% highlight ruby %}
background:linear-gradient(#fb3 50%, #58a 50%);
background-size:100% 30px;
{% endhighlight %}
可以让整个容器平铺填满这种水平纹理
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 300 200px;width: 300px;height: 195px'></div>
我们也可以创建三种颜色的纹理：
{% highlight ruby %}
background:linear-gradient(#fb3 33.3%, #58a 0, #58a 66.6%, yellowgreen 0);
background-size:100% 45px;
{% endhighlight %}
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 300 585px;width: 300px;height: 195px'></div>
<h3>垂直纹理</h3>
垂直纹理与水平纹理的代码相似，只不过渐变方向不同，对于垂直的可使用它的默认值(to bottom)
{% highlight ruby %}
background:linear-gradient( to right, #fb3 50%, #58a 0);
background-size:30px 100%;
{% endhighlight %}
<div style='background-image: url("/assets/linear-gradient.jpg"); background-position: 600 200px;width: 300px;height: 390px'></div>

<a href="http://shop.oreilly.com/product/0636920031123.do">附上《CSS Secret》</a>
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
