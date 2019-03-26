---
layout: post
title:  "CSS3-神奇的clip-path"
date:   2018-08-21 15:40:00 +0800
categories: jekyll update
---

<h1>前言</h1>
<div>之所以了解到clip-path这个属性，是因为做兼职时接到了一组动画效果。计划全部用CSS3的transition、transform、rotate等来实现，其中一个效果中文字显示像百叶窗一样，原以为实现起来很简单，可后来足足想了两天，各种Google、Baidu也没找到实现方式。然而一次刷博客，偶遇了CSS3的新属性——clip-path，灵光一现，可以用此属性来创建不规则图形，将此图形以右上角为起点往左逐渐显示文字，最终实现了效果。Happy～</div>
<img src="polygon.gif" width="220" height="220"><br>
<h1>clip-path语法</h1>
<div>
{% highlight ruby %}
clip-path: <clip-source> | [ <basic-shape> || <geometry-box> ] | none
{% endhighlight %}
其默认值是 <strong>none</strong>。另外它还有几个属性值：
<ul>
	<li><strong>clip-source：</strong>目前还没用过😄</li>
	<li><strong>basic-shape：</strong>目前只用过这个属性，可以使用一些基本的形状函数创建一些形状。主要包括`circle()`、`ellipse()`、`inset()`和`polygon()`。</li>
	<li><strong>geometry-box：</strong>是个可选参数</li>
</ul>
<h1>clip-path示例</h1>
<p>注意：使用`clip-path`需要从同一个方向绘制，因为`polygon`是一个连续线段，如果期间有交集的话，剪裁区域就会发生相减的情况。所以使用顺时针就一律顺时针，逆时针就一律逆时针。</p>
<p>鉴于经验，这里主要讲下`polygon()`函数绘制的示例：</p>
{% highlight ruby %}
div{clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);}
{% endhighlight %}
<p>见证奇迹的时刻，神奇的clip-path应用于这段代码，我们将看到一个菱形。这主要取决于函数顶点的值。下图将说明一切：</p>
<img src="polygon.png" width="300" height="300"><br>
<p>以前绘制三角形、五角形会使用 伪类 `:before`和 `:after`，现在使用`clip-path`就可以轻松搞定😉</p>
<h1>浏览器兼容性</h1>
<p>IE和Edge不支持这个属性。Firefox仅部分支持。Chrome、Safari和Opera需要使用`-webkit-`前缀支持此属性。</p>
<a href="http://bennettfeely.com/clippy/">附上一个好玩的网站，可把图片剪裁成各种图形</a>
</div>
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
