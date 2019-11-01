---
layout: post
title:  "JavaScript-将字符串转换为驼峰命名的字符串.markdown"
date:   2019-09-17 08:46:00 +0800
categories: jekyll update
---

<p>主要使用split 与 join方法</p>
{% highlight ruby %}
 $ <script type="text/javascript">
    function foo1(foo) {
        // body...
        var arr = foo.split('-');

        console.log(arr[1].charAt(0).toUpperCase() + arr[1].substring(1, arr[1].length))
        for (var i = 1; i < arr.length; i++) {
            arr[i] = arr[i].charAt(0).toUpperCase() + arr[i].substring(1, arr[i].length)
        }
        return arr.join('')

    }
    var foo = 'get-element-by-id';
    console.log(foo1(foo))
    </script>
 {% endhighlight %}

 