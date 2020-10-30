---
layout: post
title: Vue加载完成之前页面闪烁
date: 2018-03-16 18:14:24.000000000 +08:00
---
在需要元素加上：
```html
<div v-cloak>  
    {{demo}}  
</div> 
```

在css中加入：

```css
[v-cloak]{  
    display: none;  
} 
```
