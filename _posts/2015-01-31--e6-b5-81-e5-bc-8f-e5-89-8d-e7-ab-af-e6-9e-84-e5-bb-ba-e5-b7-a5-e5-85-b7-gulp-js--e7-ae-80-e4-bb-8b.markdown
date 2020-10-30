---
layout: post
title: "“流式”前端构建工具—gulp.js 简介"
date: 2015-01-31 17:34:04.000000000 +08:00
---

 

[Grunt](http://gruntjs.com/) 一直是前端领域构建工具（任务运行器或许更准确一些，因为前端构建只是此类工具的一部分用途）的王者，然而它也不是毫无缺陷的，近期风头正劲的 [gulp.js](http://gulpjs.com/) 隐隐有取而代之的态势。那么，究竟是什么使得 gulp.js 备受关注呢？


## Grunt 之殇

gulp.js 的作者 [Eric Schoffstall](http://github.com/Contra) 在他[介绍 gulp.js 的 presentation](http://slid.es/contra/gulp) 中总结了 Grunt 的几点不足之处：

1. **插件很难遵守单一责任原则**。因为 Grunt 的 API 设计缺憾，使得许多插件不得不负责一些和其主要任务无关的事情。比如说要对处理后的文件进行更名操作，你可能使用的是 `uglify` 插件，也有可能使用的是 `concat` 插件（取决于工作流的最后一个环节是谁）。  
> 我的看法：这或许是个问题，对很多人来说 Grunt 插件多少存在“职责不明”和“越俎代庖”的情况。在我看来，这也是 Grunt 一个设计思想：把对文件的操作抽象为一个[独立的组件（Files）](http://gruntjs.com/configuring-tasks#files)，任何插件都以相同的规则来使用它。遗憾在于，使用它的过程发生在每个插件的独立配置对象里，所以总给人一种“把不该这个插件做的事情丢给它来做”的别扭感觉。
2. **用插件做一些本来不需要插件来做的事情**。因为 Grunt 提供了统一的 CLI 入口，子任务由插件定义，由 CLI 命令来调用执行，因此哪怕是很简单的外部命令（比如说运行 `karma start`）都得有一个插件来负责封装它，然后再变成 Grunt CLI 命令的参数来运行，多此一举。  
> 我的看法：举双手双脚赞成！
3. **试图用配置文件完成所有事，结果就是混乱不堪**。规模较大，构建／分发／部署流程较为复杂的项目，其 `Gruntfile`有多庞杂相信有经历的人都有所体会。而 gulp.js 奉行的是“写程序而不是写配置”，它走的是一种 *node way*。  
> 我的看法：对于 node.js 开发者来说这是好事，符合他们的一贯作风；不过对于那些纯前端工程师来说（数量不小），这似乎没有什么显著的改善。况且近来 Grunt 社区涌现了不少插件来帮助开发者[组织／管理／简化臃肿的 `Gruntfile`](http://www.html5rocks.com/en/tutorials/tooling/supercharging-your-gruntfile/)，效果都还不错。所以关于这一点，就见仁见智吧。
4. **落后的流程控制产生了让人头痛的临时文件／文件夹所导致的性能滞后**。这是 gulp.js 下刀子的重点，也是本标题里“流式构建”所解决的根本问题。流式构建改变了底层的流程控制，大大提高了构建工作的效率和性能，给用户的直观感觉就是：更快。  
> 我的看法：关于流式构建，短短几句话无法讲清它的来龙去脉，但是在 node.js 的世界里，`streaming` 确实是至关重要的。我推荐一份阅读材料：[Stream Handbook](http://github.com/substack/stream-handbook)，读过之后相信心里就有数了。

作为对比和总结，作者列出了 gulp.js 的五大特点：

1. 使用 gulp.js，你的构建脚本是代码，而不是配置文件；
2. 使用标准库（node.js standard library）来编写脚本；
3. 插件都很简单，只负责完成一件事－基本上都是 20 行左右的函数；
4. 任务都以最大的并发数来执行；
5. 输入／输出（I/O）是基于“流式”的。


## gulp.js 之道

[gulp.js 的官方文档](http://github.com/gulpjs/gulp/blob/master/docs/README.md)都在 Github 上，本文是一个简介，更具体的细节还请自行阅读文档。在这里我就 gulp.js 的安装和使用流程做一个简述，先一起来领略一下 gulp.js 的风采吧。

### 第一步：安装命令行工具

```
<code class="lang-shell"><span class="hljs-variable">$ </span>npm install -g gulp
```

### 第二步：在你的项目下把 gulp 安装为开发依赖组件（假设你已经创建好了 `package.json`）

```
<code class="lang-shell"><span class="hljs-variable">$ </span>cd <<span class="hljs-constant">YOUR_PROJECT</span>>
<span class="hljs-variable">$ </span>npm install gulp --save-dev
```

### 第三步：在项目的根路径下创建 `Gulpfile.js`，初始内容为：

```
<code class="lang-javascript"><span class="hljs-keyword">var</span> gulp = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp'</span>);

gulp.task(<span class="hljs-string">'default'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
});
```

### 第四步：运行！

```
<code class="lang-shell"><span class="hljs-variable">$ </span>gulp
```

So far so good! 看起来和 Grunt 没差太远吧？的确如此，gulp.js 的学习曲线还是相当平缓的。接下来，为了能够顺利的编写构建脚本，我们来学习几个核心的 API 函数——别担心，gulp.js 的 API 非常简单，我们只需要了解四个就足以应对绝大多数的脚本编写了（而且用过 Grunt 的话，这四个都不是什么新鲜货）。

- [`gulp.task(name[, deps], fn)`](http://github.com/gulpjs/gulp/blob/master/docs/API.md#gulptaskname-deps-fn)：注册任务  
`name` 是任务名称；`deps` 是可选的数组，其中列出需要在本任务运行要执行的任务；`fn` 是任务体，这是 gulp.js 的核心了，需要花时间吃透它，[详情见此](http://github.com/gulpjs/gulp/blob/master/docs/API.md#fn)。
- [`gulp.src(globs[, options])`](http://github.com/gulpjs/gulp/blob/master/docs/API.md#gulpsrcglobs-options)：指明源文件路径  
 用过 Grunt 的话，`globs` 一定不会陌生，这里没什么变化；`options` 是可选的，具体请查看 [gulp.js API](http://github.com/gulpjs/gulp/blob/master/docs/API.md#options)
- [`gulp.dest(path)`](http://github.com/gulpjs/gulp/blob/master/docs/API.md#gulpdestpath)：指明任务处理后的目标输出路径
- [`gulp.watch(glob[, options], tasks)／gulp.watch(glob[, options, cb])`](http://github.com/gulpjs/gulp/blob/master/docs/API.md#gulpwatchglob--opts-tasks-or-gulpwatchglob--opts-cb)：监视文件的变化并运行相应的任务。你没看错，`watch` 作为核心 API 出现在 gulp.js 里了，具体用法还是要多看[文档](http://github.com/gulpjs/gulp/blob/master/docs/API.md#gulpwatchglob--opts-tasks-or-gulpwatchglob--opts-cb)，不过接下来我们会演示简单的例子。

### 范例

我们练习一个最常见的范例，写一个 node.js 程序时所需要的构建脚本。为此我们要做三件事情（括号内列出对应插件的名字，[更多插件请到此处寻找](http://gulpjs.com/plugins/)）：

1. 语法检查（`gulp-jshint`）
2. 合并文件（`gulp-concat`）
3. 压缩代码（`gulp-uglify`）

另外，我们可能还需要文件更名操作，所以 `gulp-rename` 也会很有用。接着我们需要先在项目下安装这些插件：

`<code class="lang-shell"><span class="hljs-input"><span class="hljs-prompt">$ npm install <PLUGIN_NAME></span> --save-dev</span>`

最后我们完成所有任务的编写，完整的代码如下：

```
<code class="lang-javascript"><span class="hljs-keyword">var</span> gulp = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp'</span>);
<span class="hljs-keyword">var</span> jshint = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp-jshint'</span>);
<span class="hljs-keyword">var</span> concat = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp-concat'</span>);
<span class="hljs-keyword">var</span> uglify = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp-uglify'</span>);
<span class="hljs-keyword">var</span> rename = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp-rename'</span>);

<span class="hljs-comment">// 语法检查</span>
gulp.task(<span class="hljs-string">'jshint'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
    <span class="hljs-keyword">return</span> gulp.src(<span class="hljs-string">'src/*.js'</span>)
        .pipe(jshint())
        .pipe(jshint.reporter(<span class="hljs-string">'default'</span>));
});

<span class="hljs-comment">// 合并文件之后压缩代码</span>
gulp.task(<span class="hljs-string">'minify'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
     <span class="hljs-keyword">return</span> gulp.src(<span class="hljs-string">'src/*.js'</span>)
        .pipe(concat(<span class="hljs-string">'all.js'</span>))
        .pipe(gulp.dest(<span class="hljs-string">'dist'</span>))
        .pipe(uglify())
        .pipe(rename(<span class="hljs-string">'all.min.js'</span>))
        .pipe(gulp.dest(<span class="hljs-string">'dist'</span>));
});

<span class="hljs-comment">// 监视文件的变化</span>
gulp.task(<span class="hljs-string">'watch'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
    gulp.watch(<span class="hljs-string">'src/*.js'</span>, [<span class="hljs-string">'jshint'</span>, <span class="hljs-string">'minify'</span>]);
});

<span class="hljs-comment">// 注册缺省任务</span>
gulp.task(<span class="hljs-string">'default'</span>, [<span class="hljs-string">'jshint'</span>, <span class="hljs-string">'minify'</span>, <span class="hljs-string">'watch'</span>]);
```

可以看出，基本上所有的任务体都是这么个模式：

```
<code class="lang-javascript">gulp.task(<span class="hljs-string">'任务名称'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
    <span class="hljs-keyword">return</span> gulp.src(<span class="hljs-string">'文件'</span>)
        .pipe(...)
        .pipe(...)
        <span class="hljs-comment">// 直到任务的最后一步</span>
        .pipe(...);
});
```

非常容易理解！获取要处理的文件，传递给下一个环节处理，然后把返回的结果继续传递给下一个环节……直到所有环节完成。`pipe` 就是 `stream` 模块里负责传递流数据的方法而已，至于最开始的 `return` 则是把整个任务的 `stream` 对象返回出去，以便任务和任务可以依次传递执行。

或许写成这样会更直观：

```
<code class="lang-javascript">gulp.task(<span class="hljs-string">'task_name'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span></span>{
    <span class="hljs-keyword">var</span> stream = gulp.src(<span class="hljs-string">'...'</span>)
        .pipe(...)
        .pipe(...)
        <span class="hljs-comment">// 直到任务的最后一步</span>
        .pipe(...);
    <span class="hljs-keyword">return</span> stream;
});
```

至此，你已经可以使用 gulp.js 完成绝大多数的构建工作了。下一步，我也为你准备了几条建议：

1. 花点时间浏览一下 [gulp.js 插件库](http://gulpjs.com/plugins/)，大致了解下利用已有的插件你都可以做哪些事情
2. 对于常用的插件，仔细阅读它们自己的文档，以便发挥出它们最大的功效
3. 抽时间学习 gulp.js API，特别是 `gulp.task()` 里关于任务体的详细描述，学会如何执行回调函数（callback），如何返回 `promise` 等等
4. 尝试编写适合自己工作流程和习惯的任务，如果它工作良好，把它做成插件发布给大家吧！

转至：http://segmentfault.com/blog/nightire/1190000000435599

未经允许不得转载：[空洽网](http://kongqia.com) » [“流式”前端构建工具—gulp.js 简介](http://kongqia.com/33586.html)


