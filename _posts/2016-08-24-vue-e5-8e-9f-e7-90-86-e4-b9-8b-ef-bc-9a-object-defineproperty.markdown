---
layout: post
title: Vue原理之： Object.defineProperty
date: 2016-08-24 22:44:03.000000000 +08:00
---

这个方法了不起啊。。vue.js和avalon.js 都是通过它实现双向绑定的。。而且Object.observe也被草案发起人撤回了。。所以defineProperty更有必要了解一下了几行代码看他怎么用

```
<span class="keyword">var</span> a= {}
    Object.defineProperty(a,<span class="string">"b"</span>,{
      <span class="keyword">value</span>:<span class="number">123</span>
    })
    console.log(a.b);<span class="comment">//123</span>```

很简单，，它接受三个参数，而且都是必填的。。


## 传入参数

<div>第一个参数:目标对象

第二个参数:需要定义的属性或方法的名字。

第三个参数:目标属性所拥有的特性。（descriptor）

前两个参数不多说了，一看代码就懂，主要看第三个参数descriptor，看看有哪些取值

</div>
## descriptor

<div>他又以下取值，我们简单认识一下，后面例子，挨个介绍，

value:属性的值(不用多说了)

writable:如果为false，属性的值就不能被重写,只能为只读了

configurable:总开关，一旦为false，就不能再设置他的（value，writable，configurable）

enumerable:是否能在for…in循环中遍历出来或在Object.keys中列举出来。

get:一会细说

set:一会细说

</div>### descriptor默认值

我们再看看第一个例子

```
<span class="keyword">var</span> a= {}
    Object.defineProperty(a,<span class="string">"b"</span>,{
      <span class="keyword">value</span>:<span class="number">123</span>
    })
    console.log(a.b);<span class="comment">//123</span>```

我们只设置了 value，别的并没有设置，但是  **第一次的时候** 可以简单的理解为（暂时这样理解）它会默认帮我们把writable，configurable，enumerable。都设上值，而且值还都是false。。也就是说，上面代码和下面是等价的的（  **仅限于第一次设置的时候** ）

```
<span class="keyword">var</span> a= {}
Object.defineProperty(a,<span class="string">"b"</span>,{
  <span class="keyword">value</span>:<span class="number">123</span>,
  writable:<span class="keyword">false</span>,
  enumerable:<span class="keyword">false</span>,
  configurable:<span class="keyword">false</span>
})
console.log(a.b);<span class="comment">//123</span>```

#### 以上非常重要哦。。并且以上理解对set 和 get 不起作用哦

### configurable

总开关，第一次设置 false 之后，，第二次什么设置也不行了，比如说

```
<span class="keyword">var</span> a= {}
Object.defineProperty(a,<span class="string">"b"</span>,{
  configurable:<span class="keyword">false</span>
})
Object.defineProperty(a,<span class="string">"b"</span>,{
  configurable:<span class="keyword">true</span>
})
<span class="comment">//error: Uncaught TypeError: Cannot redefine property: b</span>```

就会报错了。。注意上面讲的默认值。。。如果第一次不设置它会怎样。。会帮你设置为false。。所以。。第二次。再设置他会怎样？。。对喽，，会报错

### writable

如果设置为fasle，就变成只读了。。

```
<span class="keyword">var</span> a = {}; 

Object.defineProperty(o, <span class="string">"b"</span>, { 
    <span class="keyword">value</span> : <span class="number">123</span>,
    writable : <span class="keyword">false</span> });

console.log(a.b); <span class="comment">// 打印 37</span>
a.b = <span class="number">25</span>; <span class="comment">// 没有错误抛出（在严格模式下会抛出，即使之前已经有相同的值）</span>
console.log(o.a); <span class="comment">// 打印 37， 赋值不起作用。</span>```

### enumerable

属性特性 enumerable 定义了对象的属性是否可以在 for…in 循环和 Object.keys() 中被枚举。

```
<span class="keyword">var</span> a= {}
Object.defineProperty(a,<span class="string">"b"</span>,{
  <span class="keyword">value</span>:<span class="number">3445</span>,
  enumerable:<span class="keyword">true</span>
})
console.log(Object.keys(a));<span class="comment">// 打印["b"]</span>```

改为false

```
<span class="keyword">var</span> a= {}
Object.defineProperty(a,<span class="string">"b"</span>,{
  <span class="keyword">value</span>:<span class="number">3445</span>,
  enumerable:<span class="keyword">false</span><span class="comment">//注意咯这里改了</span>
})
console.log(Object.keys(a));<span class="comment">// 打印[]</span>```

for…in 类似，，不赘述了


## set 和 get

<div>在 descriptor 中不能  **同时** 设置访问器 (get 和 set) 和 wriable 或 value，否则会错，就是说想用(get 和 set)，就不能用（wriable 或 value中的任何一个）

set 和 get ，他俩干啥用的的，

</div>```
<span class="keyword">var</span> a= {}
Object.defineProperty(a,<span class="string">"b"</span>,{
  <span class="keyword">set</span>:function(newValue){
    console.log(<span class="string">"你要赋值给我,我的新值是"</span>＋newValue)
    },
  <span class="keyword">get</span>:function(){
    console.log(<span class="string">"你取我的值"</span>)
    <span class="keyword">return</span><span class="number">2</span><span class="comment">//注意这里，我硬编码返回2</span>
   }
})
a.b =<span class="number">1</span><span class="comment">//打印 你要赋值给我,我的新值是1</span>
console.log(a.b)    <span class="comment">//打印 你取我的值</span><span class="comment">//打印 2    注意这里，和我的硬编码相同的</span>```

简单来说，， 这个 “b” 赋值 或者 取值的时候会分别触发 set 和 get 对应的函数

这就是实现 observe的关键啊。。

转至：http://www.tuicool.com/articles/ju26riE

未经允许不得转载：[空洽网](http://kongqia.com) » [Vue原理之： Object.defineProperty](http://kongqia.com/33735.html)


