---
layout: post
title:  "JS中split,slice,splice的区别"
date:   2018-07-17 08:40:00 +0800
categories: jekyll update
---
<h1>前言</h1>
<p>工作中需要处理feed中数据，然后根据一些规则将所需字符截取出来。平常用的最多的是split，偶尔用slice，后来还了解到有splice， 单看名字会混淆，于是决定记下来，便于日后查看。</p>
<ul>
	<li>
		<p><strong>split</strong></p>
		<p>定义：该方法是切割字符串的一种方法，该方法主要用于把一个字符串分割成字符串数组并且返回新生成的数组。用于字符串对象</p>
		<p>语法：<br>
		{% highlight ruby %}str.split(separator,howmany){% endhighlight %}</p>
		<table>
			<thead>
				<th>参数</th>
				<th>描述</th>
			</thead>
			<tbody>
				<tr>
					<td>separator</td>
					<td><strong>必需</strong> 字符串或正则表达式</td>
				</tr>
				<tr>
					<td>howmany</td>
					<td><strong>可选</strong> 该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。</td>
				</tr>
			</tbody>
		</table>
		<p>返回值：一个字符串数组</p>
		<p>示例：</p>
{% highlight ruby %}
var s = "how are you";
var arr = s.split(" ");//使用" "空格来切割字符串
console.log(arr.length);// 3
console.log(arr);// how,are,you
{% endhighlight %}
	</li>
	<li>
		<p><strong>slice</strong></p>
		<p>定义：<br>该方法主要用于截取数组，并返回截取到的新数组。</p>
		<p>语法：<br>
		{% highlight ruby %}arr.slice(start,end){% endhighlight %}</p>
		<table>
			<thead>
				<th>参数</th>
				<th>描述</th>
			</thead>
			<tbody>
				<tr>
					<td>start</td>
					<td><strong>必需</strong> 从原数组中的start位置开始截取（包括下标为start的元素）。如果是负数从尾部开始截取：-1表示最后一个元素。</td>
				</tr>
				<tr>
					<td>end</td>
					<td><strong>可选</strong> 截取到指定的位置（不包括下标为end的元素）。如果没有指定，则截取到最后一个元素。注意：end要大于start，否则截取不到元素。</td>
				</tr>
			</tbody>
		</table>
		<p>返回值：一个新的数组，原数组没有做任何改变。</p>
		<p>示例：</p>
{% highlight ruby %}
var arr1 = ["a", "b", "c", "d", "e", "f"];
var newArr = arr1.slice(0, 2);
console.log(newArr);// a,b
console.log(arr1.slice(2));// c,d,e,f
{% endhighlight %}
	</li>
	<li>
		<p><strong>splice</strong></p>
		<p>定义：<br>该方法用于向数组中添加项目，或者从数组中删除项目，返回被删除的项目。</p>
		<p>语法：<br>
		{% highlight ruby %}arr.splice(index,howmany,item1,......,itemX){% endhighlight %}</p>
		<table>
			<thead>
				<th>参数</th>
				<th>描述</th>
			</thead>
			<tbody>
				<tr>
					<td>index</td>
					<td><strong>必需</strong> 整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。</td>
				</tr>
				<tr>
					<td>howmany</td>
					<td><strong>必需</strong> 要删除的项目数量。如果设置为0，则不会删除项目。</td>
				</tr>
				<tr>
					<td>item1,......itemX</td>
					<td><strong>可选</strong> 向数组添加的新项目。</td>
				</tr>
			</tbody>
		</table>
		<p>返回值：一个新的数组，包含被删除项目的新数组，如果有的话。</p>
		<p>删除示例：</p>
{% highlight ruby %}
var arr1 = ["a", "b", "c", "d", "e", "f"];
 var detailed = arr1.splice(1, 2);
console.log(arr1);// a,d,e,f
console.log(detailed);// b,c
{% endhighlight %}
<p>添加示例：</p>
{% highlight ruby %}
var arr1 = ["a", "b", "c", "d", "e", "f"];
var newArr = arr1.splice(1, 0,"m","n"); //因为第2参数为0，所以表示添加元素：从下标为1的位置插入元素。其余的元素会自动向后移动
console.log(arr1);// a,m,n,b,c,d,e,f
{% endhighlight %}
	</li>
</ul>


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
