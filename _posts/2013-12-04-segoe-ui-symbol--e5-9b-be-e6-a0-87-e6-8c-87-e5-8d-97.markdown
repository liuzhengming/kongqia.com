---
layout: post
title: Segoe UI Symbol 图标指南
date: 2013-12-04 06:14:49.000000000 +08:00
---

 


## <span style="font-size: small">有关 Segoe UI Symbol 字体</span>

添加到 Segoe UI Symbol 的大部分 UI 控件都会映射到 Unicode 专用区 (PUA)。PUA 允许字体开发人员将专用 Unicode 值分配给未映射到现有代码点的字形。当创建符号字体时这非常有用，但也会带来互操作性问题。如果字体不可用，则字形将不显示。在你可以指定 Segoe UI Symbol 字体时仅使用这些字形。

如果你使用磁贴，则无法使用这些字形，因为你无法指定磁贴字体而 PUA 字形不会通过字体回滚提供。

大部分此类字形在提供时其间距为零。你可以在每个零宽度字形上放置其他零宽度字形。例如，如果你插入零宽度的红色的实心 (U+E00B)，光标不会跑到心形的末尾，因为其宽度为零。然后，如果你插入黑色的心形轮廓 (U+E006)，则心形轮廓会放置在实心之上。

![使用零宽度字形](http://i.msdn.microsoft.com/dynimg/IC675482.png "使用零宽度字形")

大部分图标还具有镜像样式，以供使用双向文本的语言使用。

如果你使用 C#/VB/C++ 和 XAML 开发应用，则可以选择使用 [**Symbol enumeration**](http://msdn.microsoft.com/zh-cn/library/windows/apps/windows.ui.xaml.controls.symbol.aspx) 而不是 Unicode ID 从 Segoe UI Symbol 字体指定字形。如果你使用 JavaScript 和 HTML 开发应用，则可以选择使用 [**AppBarIcon enumeration **](http://msdn.microsoft.com/zh-cn/library/windows/apps/hh770557.aspx)而不是 Unicode ID 从 Segoe UI Symbol 字体指定字形。


## <span style="color: #333333;font-size: small">[]()红心大战</span>

![红心大战图标](http://i.msdn.microsoft.com/dynimg/IC632253.png "红心大战图标")


## <span style="color: #333333;font-size: small">[]()星形评级</span>

![评级图标](http://i.msdn.microsoft.com/dynimg/IC632254.png "评级图标")


## <span style="color: #333333;font-size: small">[]()复选框组件</span>

![复选框组件](http://i.msdn.microsoft.com/dynimg/IC632255.png "复选框组件")


## <span style="color: #333333;font-size: small">[]()单选按钮控件</span>

![单选按钮控件](http://i.msdn.microsoft.com/dynimg/IC632256.png "单选按钮控件")


## <span style="color: #333333;font-size: small">[]()杂项</span>

![杂项图标](http://i.msdn.microsoft.com/dynimg/IC632257.png "杂项图标")


## <span style="color: #333333;font-size: small">[]()滚动条箭头</span>

![滚动条箭头](http://i.msdn.microsoft.com/dynimg/IC632258.png "滚动条箭头")


## <span style="color: #333333;font-size: small">[]()渐进式公开箭头</span>

![渐进式公开箭头](http://i.msdn.microsoft.com/dynimg/IC632259.png "渐进式公开箭头")


## <span style="color: #333333;font-size: small">[]()后退按钮</span>

后退按钮的字形提供了 3 种不同大小，以便外环的权重等于 16pt、20pt 和 42pt。这些字形设计用于支持分层。

<table><tbody><tr><th><span style="font-size: small">16pt 代码</span></th><th><span style="font-size: small">20pt 代码</span></th><th><span style="font-size: small">42pt 代码</span></th><th><span style="font-size: small">符号</span></th><th><span style="font-size: small">描述</span></th></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A4</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0BA</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E071</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮](http://i.msdn.microsoft.com/dynimg/IC688528.png "后退按钮")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A5</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0BB</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0A6</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮轮廓](http://i.msdn.microsoft.com/dynimg/IC688529.png "后退按钮轮廓")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮轮廓</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A6</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0C4</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0A7</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮箭头](http://i.msdn.microsoft.com/dynimg/IC688530.png "后退按钮箭头")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮箭头</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A7</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0D4</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0A8</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮填充](http://i.msdn.microsoft.com/dynimg/IC688531.png "后退按钮填充")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮填充</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A8</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0B3</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E08E</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮反转](http://i.msdn.microsoft.com/dynimg/IC688532.png "后退按钮反转")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮反转</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2A9</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0AC</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0AA</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮镜像](http://i.msdn.microsoft.com/dynimg/IC688533.png "后退按钮镜像")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮镜像</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2AA</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0AD</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0AB</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮镜像箭头](http://i.msdn.microsoft.com/dynimg/IC688534.png "后退按钮镜像箭头")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮镜像箭头</span></td></tr><tr><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E2AB</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E0AF</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">U+E257</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">![后退按钮镜像反转](http://i.msdn.microsoft.com/dynimg/IC688535.png "后退按钮镜像反转")</span></td><td><span style="color: #333333;font-family: 'Open Sans', Arial, Helvetica, sans-serif;font-size: small">后退按钮镜像反转</span></td></tr></tbody></table> 


## <span style="color: #333333;font-size: small">[]() []()HTML 的后退箭头</span>

添加其他代码以创建环绕这些字形的圆环。

![HTML 的后退箭头](http://i.msdn.microsoft.com/dynimg/IC675483.png "HTML 的后退箭头")


## <span style="color: #333333;font-size: small">[]()应用栏字形</span>

在 [**AppBar**](http://msdn.microsoft.com/zh-cn/library/windows/apps/br229670.aspx) 中使用这些字形。这些字形设计为以 14pt 大小显示。使用其他代码以创建环绕这些字形的圆环。

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC687219.png "应用栏图标")

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC632264.png "应用栏图标")

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC632265.png "应用栏图标")

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC632266.png "应用栏图标")

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC688536.png "应用栏图标")

![应用栏图标](http://i.msdn.microsoft.com/dynimg/IC687221.png "应用栏图标")

未经允许不得转载：[空洽网](http://kongqia.com) » [Segoe UI Symbol 图标指南](http://kongqia.com/18152.html)


