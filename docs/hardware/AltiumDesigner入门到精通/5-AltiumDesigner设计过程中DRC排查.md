Altium Designer设计过程中DRC排查

使用AD进行电路设计，DRC检查需要注意。某些细节设置不正确时，我们会遇到各种警告语报错。

主要分为原理图设计过程中的DRC和PCB设计过程中的DRC排查。

下面以一个层次化原理图设计过程中遇到的报错为例，介绍报错排除过程。

项目名称： CT107D-V20.PrjPcb

![](media/53260091d4c0edd3b84e166cbd8b97e1.png)

打开后在项目名称处右击，“Validate PCB Project
xxx”(如果你用的是AD16之前的版本，这里是“Compile PCB ……”)

弹出Message对话框，里面有很多错误和警告：

![](media/29bdbfe3dcccd328717a8972d172b32d.png)

可以看到错误类型只有一种：“Duplicate Net Names Wire xxx”。

警告类型非常多，我们先解决报错。很多时候，错误类型解决后，警告就不存在了。之后再检查警告中比较关键的几个。

1.  “Off grid xx at xx mm,yy mm”

2.  “Footprint of component Component U18 74HC04 cannot be found”

# 原理图设计过程中的DRC检查

这个实例中，我们看到的错误是“Duplicate Net Names Wire xxx”。

首先，在“Message”中，对应的错误信息双击，原理图会自动跳到对应的出错位置。

![](media/2b07c57f5618d0cd935801422076d539.png)

可以看到： 原理图调到了OUTSIDE.SchDoc文档。

Netlabel型的名字有两个 P01, 同时，与P01连接的一个端口类型（Port）也是P01。

但实际报错指示的原理图是顶层原理图： CT107D-V20.SchDoc

![](media/53260091d4c0edd3b84e166cbd8b97e1.png)

这中错误原因一般是因为对项目选项中这两种符号的使用范围设置不正确，没有按照统一固定标准。

一般我们可以默认：

**Net Identifier Scope的下拉列表设置成了上表中的“Automatic（based on project
contents）”**

如果同时使用端口和网络标签类型：

NetLabel类型的网络标签只在同一张原理图内使用，相同的名称的放置点会在生成网表或PCB中连接在一起。

Port端口类型的用于多张原理图之间共同连接点的连接。

以上描述的适配需要在项目名称处右击：选择“Project Options”

![](media/d28bf7c6e0051744128111a6414dded1.png)

弹出对话框中，查看到这个项目的“Options”选项：

![](media/7f31a0a8418f43e455bc48b2887749b4.png)

**其中，如果Net Identifier Scope的下拉列表设置成了上表中的“Global（Netlabels and
ports global）”**

就不遵循之前默认的规则，会将项目中所有的网络标签和端口都按全局对象处理。

这时候两张原理图中，都有P00-P11的端口。而且这些网络标签又连到了同名的端口上，就会出现重复标号的问题。

解决办法1：

仍然使用**“Global（Netlabels and ports global）”:**

**将两张子原理图中任意一张，与Port相连的重复的P00-P11,Y5C名字成别的，比如：
Net00-Net11，NetY5C**

**这里我更改的是OUTSIDE.SchDoc：**

**![](media/12592354fd1215e0373ffecd9f985388.png)**

**更改之后重新验证：**

**Message提示：**

**![](media/8a500f30f2d5c1f1475dfbdefc6b288a.png)**

**这个地方比较奇怪，只有一个P02报错。**

**其它的都解决了。双击报错的信息。软件自动打开报错的原理图。**

**![](media/6e9ef3bf8380f8595120a2a2385b5226.png)**

**这些地方是有P02网络标签的地方。看不出错误，怀疑是连接时，格点设置不合适，导致看起来标签和线连接了，实际没有连接。**

**把这些标签和对应的线删除，重新验证，这个错误消失。**

**重新设置格点：2.54mm(100mil),重新将刚刚删除的连线和标签加上。**

**验证后，没有错误信息出现。**

**到这里，这些错误就解决了。但我并不推荐这种方式。因为这样的设计方式，看图时会比较混乱，同一个NetLabel可能会出现在不同的原理图中，看图非常不方便。推荐使用下面的方式。**

解决办法2：

使用**“Automatic (Based on project contents)”**

这时候，我们需要遵循，网络标号（NetLabel）只在同一张原理图中出现，用来进行节点的连接，而跨原理图进行连接时，我们使用下面三种方式之一：

1.  Ports(端口)：这种最方便，也便于在层次化原理图中使用。

2.  Signal Harness（信号线束类型）：
    这个用起来稍微麻烦些，建议参考官方的层次化原理图进行探索。

3.  Off Sheet Connector(跨原理图连接符)：
    用这个可以专门连接不同页原理图之间的引脚

    个人总结：

    我们如果将一张（子）原理图抽象成一个封装好的芯片，原理图里的元器件相当于芯片内部的晶体管等基础组件，Netlabel类型和wire类型相当于器件内部的连线。Port端口类型，相当于我们将芯片封装后给用户开放的芯片引脚。

    这样，一张子原理图就相当于我们自己封装的有一定功能的“元器件”，我们在进行系统化设计和层次化设计时，就可以调用之前设计的可以重复利用的子原理图了。

    下面介绍怎么用这种方式调整刚才的项目。

    首先，将**Net Identifier Scope的下拉列表设置成了上表中的“Automatic(based on
    project contens)”**

    ![](media/b22cb6d56e7ecd5f36a27aec0ebb0d74.png)

    然后，在项目名称处，右击进行“Validate PCB Project CT107D-V20.PrjPcb”

    这个时候，Message中的报错如下：

    ![](media/a71d75521f720d9ce9cc35d24bf630a5.png)

    这个原因是因为这几个Netlabel在不同的原理图中出现，将他们换成对应类型的Port类型既可以解决。

    在OUTSIDE.SchDoc中，
    P20/SCL和P21/SDA的网络标号和MCU.SchDoc中的多个P20/SCL和P21/SDA 重名了。

    ![](media/d010ecaef61c29ab5a2ba8ee404d6dd8.png)

    MCU.SchDoc中：

    ![](media/a4d2d6dc6bf69062db45514e1c54e339.png)

    然后在顶层原理图对应的方块电路右击，选择“Synchronize Sheet Entries and
    Ports”

    ![](media/0b42aa5fced62b7d0a653653e73c5ecb.png)

    ![](media/6a0e39efecc3fe5854953cc81c11751e.png)

    鼠标会变成光标，带着两个端口出现在对应的方块电路中，点击放置，并进行连线。完成后，顶层方块电路中会出现一组P20/SCL和P21/SDA的新端口。

    ![](media/7e110426a23d9aa3bf39d07aa5c9956e.png)

    在进行验证，错误里就没有这对端口的错误了：

    ![](media/e9af2df90fbb655235d535f7a1e2de63.png)

    上面显示还剩四个错误，这四个错误的处理方式和刚才一样，将对应的NetLabel
    换成Port进行连接即可解决问题。

    ![](media/d79d1052d67fb37aba0f1b35cf1fd1cd.png)

    修改为成的顶层如下：

    ![](media/04ba25ead287faa30f092eedcb758439.png)

    在进行编译验证，只剩一种类型的警告，并提示没有错误：

    ![](media/518c32d9e153ece460aa9790280c3edb.png)

    警告信息暂时可以忽略。
