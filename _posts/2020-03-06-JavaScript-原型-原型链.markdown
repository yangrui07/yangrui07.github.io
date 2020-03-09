---
layout: post
title:  "JavaScript-原型-原型链"
date:   2020-03-06 16:51:00 +0800
categories: jekyll update
---
<h1>1、原型</h1>
<p>对象的原型是用来继承属性的，有显示原型与隐形原型之分</p>
{% highlight ruby %}
 $ function Fn(){}
 $ var fn = new Fn()
 {% endhighlight %}
<ul>
    <li>每个函数function都有一个prototype，即显示原型 Fn.prototype。其默认值是一个空的Object对象</li>
    <li>每个实例对象都有一个__proto__，即隐式原型 fn.__proto__</li>
    <li>每个函数function的显示原型就等于其实例对象的隐式原型，即Fn.prototype === fn.__proto__</li>
</ul>
<h1>2、原型链</h1>
<ul>
    <li>别名：隐式原型链（沿着__proto__查找）</li>
    <li>作用：查找对象的属性（方法）</li>
    <li>查找过程：
    <ul>
      <li>访问一个对象的属性时，先在自身属性中查找，找到返回</li>
      <li>如果在自身属性中没有找到，再沿着__proto__这条链向上查找，找到返回</li>
      <li>如果最终没有找到，则返回undefined</li>
    </ul>
    </li>
</ul>
 

 