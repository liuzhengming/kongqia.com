---
layout: post
title: 纯css改变select的样式
date: 2018-03-02 10:09:59.000000000 +08:00
---
原理是将浏览器默认的下拉框样式清除，然后应用上自己的，再附一张向右对齐小箭头的图片即可。

```css
select {
  /*Chrome和Firefox里面的边框是不一样的，所以复写了一下*/
  border: solid 1px #000;

  /*很关键：将默认的select选择框样式清除*/
  appearance:none;
  -moz-appearance:none;
  -webkit-appearance:none;

  /*在选择框的最右侧中间显示小箭头图片*/
  background: url("http://ourjs.github.io/static/2015/arrow.png") no-repeat scroll right center transparent;


  /*为下拉小箭头留出一点位置，避免被文字覆盖*/
  padding-right: 14px;
}


/*清除ie的默认选择框样式清除，隐藏下拉箭头*/
select::-ms-expand { display: none; }
```

转至：http://ourjs.com/detail/551b9b0529c8d81960000007
