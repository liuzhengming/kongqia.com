---
layout: post
title: vue动画
date: 2018-09-17 19:38:57.000000000 +08:00
---
### CSS 动画
例子：
<iframe width="100%" height="300" src="//jsfiddle.net/liuzhengming/nfe0b2zw/embedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>


例子：
<iframe width="100%" height="300" src="//jsfiddle.net/liuzhengming/38hfqzr0/embedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

### 在进入/离开的过渡中，会有 6 个 class 切换。
1. v-enter：定义进入过渡的开始状态。在元素被插入之前生效，在元素被插入之后的下一帧移除。
2. v-enter-active：定义进入过渡生效时的状态。在整个进入过渡的阶段中应用，在元素被插入之前生效，在过渡/动画完成之后移除。这个类可以被用来定义进入过渡的过程时间，延迟和曲线函数。
3. v-enter-to: 2.1.8版及以上 定义进入过渡的结束状态。在元素被插入之后下一帧生效 (与此同时 v-enter 被移除)，在过渡/动画完成之后移除。
4. v-leave: 定义离开过渡的开始状态。在离开过渡被触发时立刻生效，下一帧被移除。
5. v-leave-active：定义离开过渡生效时的状态。在整个离开过渡的阶段中应用，在离开过渡被触发时立刻生效，在过渡/动画完成之后移除。这个类可以被用来定义离开过渡的过程时间，延迟和曲线函数。
6. v-leave-to: 2.1.8版及以上 定义离开过渡的结束状态。在离开过渡被触发之后下一帧生效 (与此同时 v-leave 被删除)，在过渡/动画完成之后移除。

### 自定义过渡的类名

我们可以通过以下特性来自定义过渡类名：

+ enter-class
+ enter-active-class
+ enter-to-class (2.1.8+)
+ leave-class
+ leave-active-class
+ leave-to-class (2.1.8+)

Animate.css 结合

<iframe width="100%" height="300" src="//jsfiddle.net/liuzhengming/vLwy9pmr/embedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>


### 可以在属性中声明 JavaScript 钩子

<iframe width="100%" height="300" src="//jsfiddle.net/liuzhengming/msgk52y7/embedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

https://cn.vuejs.org/v2/guide/transitions.html
