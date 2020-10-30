---
layout: post
title: Gmat使用说明-运行Gmat进行简单轨道转移
date: 2015-11-24 01:06:12.000000000 +08:00
---

空间任务设计中一个常见问题是从一个圆轨道到另一个圆轨道的共面转移。圆共面转移用于提升受大气阻力影响退化的近地轨道，也用于从近地轨道转移到地球同步轨道，或将飞行器送到火星。一个著名的机动序列是霍曼转移，用最少的燃料，完成圆形共面转移。霍曼转移包括两个机动。第一次机动是将轨道最远点提高（或将最近点降低）到指定的高度，并将飞行器置于椭圆轨道中。在椭圆转移轨道的最远点（或最近点），运用第二次机动，在最后的高度将轨道编程圆轨道。

以霍曼转移为例，将轨道从近地轨道转移到地球同步任务轨道。步骤如下：

1）创建并配置一个DifferentialCorrectors资源。

2）修改DefaultOrbitView，可视化轨迹。

3）创建两个默认推进器资源。

4）创建两个目标序列：a：提升轨道最远点到地球同步轨道高度；b：将轨道变为圆轨道。

5）运行任务并分析结果。

**1.设置机动、差分校正器及图形化**

准备工作：打开GMAT，加载默认任务；使用默认飞行器DefaultSC、默认预报器DefaultProp、以及两个机动。

**1.1创建差分校正器**

在左侧窗口资源标签下的资源树中，展开Solvers，右键Boundary Value Solvers，点击Add->DifferntialCorrector；创建名为DC1的资源。

**1.2修改默认轨道视图**

需要对DefultOrbitView做镜像修正，保证轨道的末状态能够完全在窗口中展现出来。

1）在资源树中，双击DefaultOrbitView，打开属性界面。

2）在Drawing Option标签下方的Solver Iterations右侧下拉列表中，选择Current。

3）在View Up Definition标签下的Axis右侧下拉列表中，选择X。

4）在View Definition标签下的View Point Vector右侧三个框中，分别填写0、0、120000。

5）点击OK保存。

[![图片1](http://kongqia.com/wp-content/uploads/2015/11/图片12.png)](http://kongqia.com/wp-content/uploads/2015/11/图片12.png)图1 修改默认轨道视图

**1.3创建机动**

1）在左侧窗口资源标签下的资源树中，右键DefaultIB，点击Rename，在输入框中输入TOI，点击OK。

2）在左侧窗口资源标签下的资源树中，右键Burns文件夹，点击Add->ImpulsiveBurn，创建ImpulsiveBurn1，按1）中方法将其重命名为GOI。

**2.配置任务序列**

创建一个初始预报命令，再创建目标序列本身，再创建结束预报命令。

**2.1配置初始预报命令**

1）在左侧窗口任务标签下的任务树中，将Propagate1设置为预报DefaultSC.Earth.Periapsis。

2）将Propagate1重命名为Prop To Periapsis。

**2.2创建目标序列**

1）在左侧窗口任务标签下的任务树中，右键Prop To Periapsis->Insert Afer->Target，将产生两个独立的命令：Target1和End Target1，重命名Target1为Hohmann Transfer。

2）右键Hohmann Transfer->Append->Vary，产生Vary1，重命名Vary1为Vary TOI。

3）重复2）中做法，Append->Maneuver，重命名为Perform TOI。

4）重复2）中做法，Append->Propagate，重命名为Prop To Apoapsis。

5）重复2）中做法，Append->Achieve，重命名为Achieve RMAG = 42165。

6）重复2）中做法，Append->Vary，重命名为Vary GOI。

7）重复2）中做法，Append->Maneuver，重命名为Perform GOI。

8）重复2）中做法，Append->Achieve，重命名为Achieve ECC = 0.005。

**2.3创建结尾预报器命令**

1）在左侧窗口任务标签下的任务树中，右键End Hohmann Transfer->Insert After->Propagate，将产生一个新的Propagate3，重命名为Prop One Day。

2）双击Prop One Day，打开属性编辑页，在Condition列中，将12000.0更改为86400（一天的秒数），点击OK保存设置。

3）完成上述操作后，效果如图2所示。

[![图片2](http://kongqia.com/wp-content/uploads/2015/11/图片21.png)](http://kongqia.com/wp-content/uploads/2015/11/图片21.png)图2 创建目标序列

图2列表中，两个Maneuver用来设定可用的控制；两个Vary及两个Achieve用来设定需要满足的条件。

**2.4设置目标序列**

以上已经创建了任务序列框架，还需要对目标序列变量进行设置。

**2.4.1设置Vary TOI命令**

1）双击Vary TOI，打开属性编辑页。可以看到在Vriable框中值为TOI.Element1，默认为VNB(Velocity-Normal-Binormal)坐标系下的TOI速度值，保留这个值。

2）在Initial Value框中，填入1.0。

3）在Max Step框中，填入0.5。

4）点击OK，保存设置。

[![图片3](http://kongqia.com/wp-content/uploads/2015/11/图片31.png)](http://kongqia.com/wp-content/uploads/2015/11/图片31.png)图3 设置Vary TOI属性

**2.4.2设置Perform TOI命令**

1）双击Perform TOI，打开属性编辑页。可以看到Burn设置为TOI，Spacecraft设置为DefaultSC，满足设置，不需要更改。

2）点击OK，保存设置。

[![图片4](http://kongqia.com/wp-content/uploads/2015/11/图片41.png)](http://kongqia.com/wp-content/uploads/2015/11/图片41.png)图4 设置Perform TOI属性

**2.4.3设置Prop To Apoapsis命令**

1）双击Prop To Apoapsis，打开属性编辑页。

2）在Parameter下，将DefaultSC.ElapsedSecs替换为DefaultSC.Earth.Apoapsis。

3）点击OK，保存设置。

[![图片5](http://kongqia.com/wp-content/uploads/2015/11/图片51.png)](http://kongqia.com/wp-content/uploads/2015/11/图片51.png)图5 设置Prop To Apoapsis

**2.4.4设置****Achieve RMAG = 42165****命令**

1）双击Achieve RMAG = 42165，打开属性编辑页。

2）可以看到目标设置为DefaultSC.Earth.RMAG，这个是我们所需要的，因此不作更改。

3）在Value框中，输入42164.169，是更为精确的地球同步轨道半径，单位为km。

4）点击OK保存设置。

[![图片6](http://kongqia.com/wp-content/uploads/2015/11/图片61.png)](http://kongqia.com/wp-content/uploads/2015/11/图片61.png)图6 设置Achieve RMAG = 42165

**2.4.5设置Vary GOI命令**

1）双击Vary GOI，打开属性编辑页。

2）点击Variable框右侧的Edit，打开参数选择页，如图7所示。在左侧Object List中，选择GOI，Object Properties中，双击Element1，将其添加到右侧Selected Value(s)，点击OK确定。

[![图片7](http://kongqia.com/wp-content/uploads/2015/11/图片7.png)](http://kongqia.com/wp-content/uploads/2015/11/图片7.png)图7 Vary GOI参数选择页

3）在Initial Value框中，填写1.0；在Max Step中，填写0.2；点击OK保存设置。

[![图片8](http://kongqia.com/wp-content/uploads/2015/11/图片8.png)](http://kongqia.com/wp-content/uploads/2015/11/图片8.png)图8 Vary GOI属性设置

**2.4.6设置Perform GOI命令**

1）双击Perform GOI，打开属性编辑页。

2）在Burn右侧的下拉列表中，选择GOI。

3）点击OK保存设置。

[![图片9](http://kongqia.com/wp-content/uploads/2015/11/图片9.png)](http://kongqia.com/wp-content/uploads/2015/11/图片9.png)图9 Perform GOI设置

**2.4.7设置Achieve ECC = 0.005命令**

1）双击Achieve ECC = 0.005，打开属性编辑页。

2）点击Goal右侧的Edit，打开ParameterSelectDialog，在Object Properties列表中，选择ECC，双击。

3）在Value框中，输入0.005。

4）在Tolerance框中，输入0.0001。

5）点击OK保存设置。

[![图片10](http://kongqia.com/wp-content/uploads/2015/11/图片10.png)](http://kongqia.com/wp-content/uploads/2015/11/图片10.png)图10 Achieve ECC = 0.005设置

**3.运行任务**

点击保存按钮，将任务保存在合适的路径。

点击运行，观察任务运行。

[![图片11](http://kongqia.com/wp-content/uploads/2015/11/图片111-595x325.png)](http://kongqia.com/wp-content/uploads/2015/11/图片111.png)图11 任务运行视图

未经允许不得转载：[空洽网](http://kongqia.com) » [Gmat使用说明-运行Gmat进行简单轨道转移](http://kongqia.com/33642.html)


