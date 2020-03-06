---
layout: post
title:  "JavaScript-检测数据类型的方法"
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
 {% highlight ruby %}
$ function A(){}
$ function B(){}
$ var o = new A()
$ o instanceof A -> true
$ o instanceof B -> false
 {% endhighlight %}
<p>该方法对于Array、Date、String、RegExp、Error会出现如下情况：</p>
  {% highlight ruby %}
$ [] instanceof Array -> true
$ [] instanceof Object -> true
$ new Date() instanceof Date -> true
$ new Date() instanceof Object -> true
 {% endhighlight %}
 <p>该方法也无法判断由字面量创建的对象</p>
  {% highlight ruby %}
$ 1 instanceof Number -> false
$ new Number(1) instanceof Number -> true
 {% endhighlight %}
<p>该方法无法检测null和undefined</p>
  {% highlight ruby %}
$ null instanceof null
$ Uncaught TypeError: Right-hand side of 'instanceof' is not an object
$ undefined instanceof undefined
$ Uncaught TypeError: Right-hand side of 'instanceof' is not an object
 {% endhighlight %}
<h1>3、constructor </h1>
 {% highlight ruby %}
$ (1).constructor === Number -> true
$ (new Number(1)).constructor === Number -> true
$ (new Date()).constructor === Date -> true
$ (new Date()).constructor === Object -> false
 {% endhighlight %}
 <p>该方法无法检测null和undefined</p>
  {% highlight ruby %}
$ null.constructor === null
$ Uncaught TypeError: Cannot read property 'constructor' of null
$ undefined.constructor === undefined
$ Uncaught TypeError: Cannot read property 'constructor' of undefined
 {% endhighlight %}
  <p>缺点：若把对象的原型prototype修改的话，检测结果就不同了。比如下面的情况：</p>
{% highlight ruby %}
$ function C(){}
$ C.prototype = new Date()
$ var d = new C()
$ d.constructor === Function -> false
$ d.constructor === Date -> true
 {% endhighlight %}
<h1>4、Object.prototype.toString().call() </h1>
 {% highlight ruby %}
$ Object.prototype.toString.call(1) -> [object Number]
$ Object.prototype.toString.call('') -> [object String]
$ Object.prototype.toString.call(true) -> [object Boolean]
$ Object.prototype.toString.call(null) -> [object Null]
$ Object.prototype.toString.call(undefined) -> [object Undefined]
$ Object.prototype.toString.call(new Date()) -> [object Date]
$ Object.prototype.toString.call(new Function()) -> [object Function]
$ Object.prototype.toString.call({}}) -> [object Object]
$ Object.prototype.toString.call(new Object()) -> [object Object]
 {% endhighlight %}
 <p>全能方法，可准确判断出数据类型</p>
<h1>4、总结 </h1>
<table>
    <thead>
        <th>判断方法</th>
        <th>缺点</th>
    </thead>
    <tbody>
        <tr>
            <td>typeof</td>
             <td>无法判断null，无法区分Array和Date等</td>
        </tr>
        <tr>
            <td>instanceof</td>
             <td>无法检测null和undefined，对于字面量方式创建的基本数据类型无法判断</td>
        </tr>
         <tr>
            <td>constructor</td>
             <td>无法检测null和undefined，若对象的原型被修改，检测结果就不同了</td>
        </tr>
        <tr>
            <td>Object.prototype.toString().call()</td>
             <td>无</td>
        </tr>
    </tbody>
</table>

 