---
layout: post
title:  "2018-07-17-JS-slice-splice-split的区别"
date:   2018-07-17 08:40:00 +0800
categories: jekyll update
---
<h1>JS中slice,splice,split的区别</h1>
<p>工作中需要处理feed中数据，然后根据一些规则将所需字符截取出来。用的最多的是split，偶尔用slice，后来还了解到有splice， 单看名字会混淆，于是决定记下来，日后在混淆的时候便于查看。</p>
<ul>
	<li>
		<p><strong>split</strong></p>
		<p>定义：split是切割字符串的一种方法，该方法主要用于把一个字符串分割成字符串数组并且返回新生成的数组</p>
		<p>用法：<br>
		{% highlight ruby %}str.split(separator,howmany){% endhighlight %}</p>
		<table>
			<thead>
				<th>参数</th>
				<th>描述</th>
			</thead>
			<tbody>
				<tr>
					<td>separator</td>
					<td><strong>必需</strong>字符串或正则表达式</td>
				</tr>
				<tr>
					<td>separator</td>
					<td><strong>可选</strong>该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。</td>
				</tr>
			</tbody>
		</table>
		{% highlight ruby %}
		var s = "how are you";
		var arr = s.split(" ");//使用" "空格来切割字符串
		console.log(arr.length);// 3
		console.log(arr);// how,are,you
		{% endhighlight %}
	</li>
	<li>
		<p><strong>slice</strong></p><strong></strong>
		<p></p>
	</li>
	<li>
		<p><strong>slice</strong></p><strong></strong>
		<p></p>
	</li>
</ul>


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
