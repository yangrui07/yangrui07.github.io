---
layout: post
title:  "JavaScript-检测数据类型的方法"
date:   2020-02-15 18:09:00 +0800
categories: jekyll update
---
<h1>1、typeof</h1>
<p>它返回一个表示数据类型的字符串，返回结果包括：</p>
<ul>
    <li>number</li>
    <li>string</li>
    <li>boolean</li>
    <li>undefined</li>
    <li>function</li>
    <li>object</li>
</ul>
{% highlight ruby %}
 $ typeof 1 -> number
 $ typeof '' -> string
 $ typeof true -> boolean
 $ typeof undefined -> undefined
 $ typeof new Function() -> function
 $ typeof null -> object
 $ typeof {} -> object
 $ typeof [] -> object
 $ typeof new Date() -> object
 $ typeof new Number(1) -> object
 {% endhighlight %}
 <p>不能判断出null</p>
 <p>除了function以外的对象都会被识别为object，不能区分Array和Date等</p>
<h1>2、instanceof</h1>
<p>用来判断A是否是B的实例</p>
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

 