# Altium Designer PCB设计

PCB设计是电子产品的设计中不可缺少的重要环节。原理图设计的再完美，如果电路板PCB
Layout设计不合理,产品的性能将大打折扣，甚至不能正常工作。

做好PCB Layout的第一步就是要熟练使用PCB设计工具。我的这篇文章首先要分享Altium
Designer 的PCB设计步骤。

## Altium Designer PCB编辑器的功能介绍

AD20的PCB设计能力非常强，能够支持最高复杂的32层的PCB设计。

1.  **任意角度布线**：在高密度板上绕开障碍物进行专业操作，并且深入到您的BGA中走线，从而无需额外的信号层。借助智能避障算法，您可以使用切向弧避开障碍物，从而最有效地利用您的电路板空间。

2.  **走线的平滑处理：**对走线进行编辑以改善信号完整性是很耗费时间的，尤其是当您必须对单个弧线以及蛇形调整线进行编辑的时候。这就是为什么Altium
    Designer
    20合并了新的布线优化引擎和高级的推挤功能以帮助加快该过程，从而提高生产率的原因。

3.  **交互式属性面板：**通过更新的属性面板可以完全清晰地操控设计对象和功能。实时查看相关属性，供应商信息，甚至生命周期信息。

4.  **基于时间的匹配长度：**高速数字电路取决于准时到达的信号和数据。如果走线调整不当，飞行时间会有所变化，并且数据错误可能会很多。Altium
    Designer 20计算走线上的传播时间，并为高速数字信号提供同步的飞行时间。

5.  **爬电距离规则：**当目标信号之间通过非导电表面和电路板边缘区域的爬电距离等于或小于指定的爬电距离时，该设计规则将标记出违规。

6.  **返回路径检查：**除非提供适当的返回路径，否则高速信号会产生电磁场，这可能导致串扰，数据错误或辐射干扰。正确的返回路径可使噪声电流通过非常低的阻抗返回到地，从而消除了这些问题。Altium
    Designer 20
    将监视返回路径并检查所有参考多边形的返回路径完整性，因此您无需手动执行此操作。

7.  **新的原理图增强：**Altium
    Designer在其原理图编辑器上进行了改进，引入了新的DirectX引擎，即时编译功能以及更加简化的交互式属性面板。

8.  **合理的自动布线功能：**在自动布线过程中，AD可以基于计算机中定义的规则，并给予网络形状对电路板进行自动布线。自动布线可以在某个网络、某个特殊区域甚至整个电路板的范围内进行，这些可以大大减轻用户的工作量，提高设计效率。

## PCB编辑器界面简介

PCB编辑器主界面分：主菜单栏，主工具栏，主工作面板。

![](media/8a09a0a5bc25a1d3b7bc8463c3fb3682.png)

1.  

2.  

### 主菜单栏

PCB设计过程中的操作都可以通过主菜单中对应的菜单命令完成。主要菜单命令大类如下：

![](media/283417c5a40bd2fdfa16a2111b7909c1.png)

“File(文件)”：所有文件操作-新建，打开，导入，导出，关闭等操作。

“Edit(编辑)”：对象选择，复制，粘贴，查找与编辑等操作。

“View(查看)”：视图操作的管理与切换等

“Project(项目)”：项目的相关操作。

“Place(放置)”：放置PCB Layout过程中的对象等。

“Design(设计)”：PCB
Layout过程中的规则建立，交换操作，板型定义，元件库生成等操作。

“Tools(工具)”：设计过程中的各种工具。

“Route(布线)”：各种布线操作命令。

“Reports(报告)”：生成报告相关的命令。

“Window(窗口)”：窗口操作命令。

“Help(帮助)”：帮助菜单命令。

### 主工具栏

PCB设计工作面板中，有一个常用工具的工具栏，如下：

![](media/6267caa83fd4075d4946fadfe86c793c.png)

这常用的14个分类的工具主要功能：

1.  选择过滤器

2.  Objects for snapping

3.  Move Object

4.  选择重叠对象的操作

5.  对其操作

6.  放置器件及3D操作

7.  交互式布线

8.  交互式线长调整

9.  过孔和焊盘放置

10. 放置多边形

11. 放置Keepout(线，框，块等)

12. 测量工具

13. 文本工具

14. 绘图工具

## PCB的设计流程

PCB设计遵循一定的设计流程，能够降低设计过程中出错的概率。下面是我总结的一种设计流程：

![](media/a3fe60504a93cfaef1209f52e5d50fad.png)

项目准备：应准备好PCB项目和已经完成的原理图图纸。

资料准备：编译通过的项目，封装库，结构图(摆放位置及Dxf文件)，设计说明(关键信号处理及制板工艺说明)，重要器件数据手册(推荐布局布线等参考)。

## PCB文件的建立

在打开的项目中，通过“File”-“New”-“PCB”来创建PCB文件。

然后保存PCB文件为需要的名字。

## PCB的物理结构与参数设置

大多数厂家默认使用Mechanical 1
作为电路板的物理边界即板子的边框层。以前很多人使用Keepout层做边框，但这种方式不太标准，不太推荐这种方式。

这个边框层我们可以手动在PCB编辑器环境中利用绘图工具绘制，但更多情况下由结构工程师导出的结构设计图纸(.dxf)文件导入，然后选中边框，使用“Design”-“Board
Shape”-“Define from selected objects”。(快捷键英文输入法： D + S + D)。

其他功能暂时不介绍。

![](media/0714a7f7e02b15d25f15bf774325184d.png)

定义完成后：

![](media/7c7051fd5bb98d7b4de13e5e57c889b1.png)

在PCB界面，按键盘上的“L”键，弹出PCB层叠功能设置。“View Configuration”

在“Layer\&Colors”可以设置每层使用的颜色。

![](media/63dff5536992bf7a8b93148fa44ae6eb.png)

分层的类别说明：

1.  Signal Layers(信号层)：实际要使用的铜箔布线层

2.  Internal
    Planes(内部电源层或者地平面层)：这部分也属于铜箔层，主要用于建立电源和地网络。

3.  Mechanical
    Layers(机械层)：用于描述机械结构、标注及加工等说明的参数都放在这层。不能完成电气连接特性。

4.  Mask
    Layers(阻焊层)：这部分主要用于保护铜线，也可以防止器件被焊到不正确的地方。这里有

5.  Silkscreen Layers(丝印层)：

6.  Other Layers(其它层)：

“View Options”可以设置PCB的可视化参数属性。(如透明度等)。

![](media/28443179f009584c65f91a06ff16ff2a.png)

在PCB界面，进行PCB层叠参数设置时，使用命令：“Design”-“Layer Stack
Manager”，弹出Stackup。设置层叠，阻抗，过孔属性。

![](media/da3eeda443b52524007948191ede9204.png)

如果想要设计柔性板或者刚柔结合电路板，需要在这里设置。之后会有具体的项目讲解。

## PCB中导入原理图网络表

以一个项目：STM32F103CxT6-V1I0.PrjPcd为例。

在原理图设计完成的情况下，要进行PCB
Layout导入网表前，应该将原理图中所用到的所有元件库进行装载。

可以在“Tools” – “Foot Print Manager”中，查看和修改元器件选用的封装。

![](media/2a3a32fb746948c664859902117ccf37.png)

当封装选择完成后，在“Design”-“Update Schematics in xxxx.PrjPcb”。

![](media/a13ab59a50b40017389ebfe1a9bb7126.png)

弹出对话框：点击“Validate
Changes”可以验证，Check栏会显示状态。如图中，有红色叉的后面提示封装没有找到，这时候需要检查是否添加了正确的封装。

全部添加后，点击“Execute Changes”会有在Done栏会显示状态。

![](media/62964c89f6b5ffa5374e5fdcd050bade.png)

全部验证完成并正确后，PCB文档中会导入元器件：

![](media/151a6b7797e1a1e0aa6ee8eaf3b9430d.png)

## PCB编辑器的操作

1.  

2.  

3.  

4.  

5.  

6.  

7.  

### 视图的移动

1.  类似原理图试图移动方式，右击鼠标键，按下至出现小手符号，就可以任意拖动视图。

2.  鼠标滚轮上下滚动可以将视图上下移动；按住Shift，上下滚动鼠标滚轮，视图将左右移动。

### 图纸的缩放

1.  类似原理图中，使用“Page Up”和“Page Down”放大和缩小

2.  使用菜单中的“View”-“Zoom In”和“Zoom Out”

3.  按住“Ctrl”+ 鼠标滚轮上下滚动

4.  安装鼠标中间的滚轮，前后拖动可以放大和缩小

### 整体显示

使用快捷键：V + F（适合文档） / V + D（整个文档） / V + A(区域)

## 元件的布局

1.  

### 快速自动布局

AD提供了很方便的交互式布局与布线的功能，在我们设计原理图时，最好就开始构思PCB的布局。这样，我们在进行PCB布局时，可以利用原理图与PCB的“Tools”-“Cross
Select Mode”，从大量元器件中快速选出相关联的或者需要几种摆放的元器件。

1.  选中目标器件

    在原理图中快速选择元器件，我们可以使用“Property ”面板的“Selection
    Filter”或工具栏快速筛选过滤器，只选择： Components

    ![](media/fc2d947790f26bb15ceb025bdb070c74.png)

    在原理图中，单击鼠标左键不放，选中要布局或者筛选的元件区域，可以只选择该区域的元器件。此时打开PCB编辑器，对应的元器件也自动被选中。

    ![](media/3423e5179206d7966c07a7638594a6a7.png)

2.  自动布局

    然后，在PCB编辑器内，选择“Tools”-“Component Placement”-“Arrange Within
    Rectangle”。

    ![](media/56a8df3e8d51c350c14275206025760d.png)

    鼠标光标变成十字，选择一个要放置元件的区域，绘制一个方框，会发现刚刚选中的元件都被自动放置到了刚绘制的方框中。

![](media/bc5924639109d8d86380c088fe999a58.png)

这样我们可以将一张原理图中的元件快速筛选出来并进行初步布局。

当时用层次化原理图时，默认会为每张原理图生成一个Room,同一张原理中的元件会在同一个Room中。这时候，我们可以直接在PCB编辑器中，使用：“Tools”-““Component
Placement”-“Arrange Within Room”，光标变成十字单击对应的Room。

![](media/2a1eaa72acba4c7404835bf4077a4535.png)

软件会对这个Room中的元件进行快速自动布局。

![](media/a0c5e5260b0eb8c683d52e2923c76ecc.png)

通过这两部操作后，我们可以将复杂的电路元件，在PCB编辑器中快速的分区放置。以加快后期手动布局。

### 手动布局

在进行完快速自动布局后，我们需要对布局进行手动优化，细化调整各类元件的位置和方向等。

1.  元器件的对齐

    在选中几个需要对齐放置的元件时，使用对齐命令或者工具，可以很方便的将PCB布局优化的更加“整齐”、“对称”和“美观”，也会方便后期进行布线操作，提高板子的布通率。

    在选中的元器件上，右击，选择“Align”-对应的对齐命令。

    ![](media/ace38e3d566c76d73481b6e0aa413dc2.png)

    也可以右击击工具栏的对齐工具，选择合适的命令执行。

2.  元器件丝印文字位置

    当我们完成布局后，通常需要调整丝印文字的位置。我们可以使用对齐命令中的“Position
    Component Text”完成。

    ![](media/aa5a46690d626936b9f33744a0d9a89f.png)

    首先选中所有的要进行调整的文字，可以选中一个，然后右击使用“Find Similar
    Objects”快速选出具有相同属性的对象（在这里选中的是Designator）。

    然后，选择“Align”-“Position Component Text”。弹出设置对话框。

    ![](media/15235caf4d804023caa2d4812fd883ae.png)

    可以设置“Designator”和“Comment”的位置。

3.  元器件间距调整

    元器件间距的调整主要包括：水平方向和垂直方向的调整。

    这些命令也在“Align”中，主要包括：

    ![](media/c694c9fb3831ba749100c63316a7c458.png)

    “Align Horizontal Centers”:水平中心对称分布

    “Distribute Horizontally”: 水平分布

    “Increase Horizontal Spacing”:增加水平间距。

    “Decrease Horizontal Spacing”: 增加水平间距。

    “Align Vertical Centers”: 垂直中心对称分布

    “Distribute Vertically”: 垂直分布

    “Increase Vertical Spacing”:增加垂直间距。

    “Decrease Vertical Spacing”: 增加垂直间距。

4.  移动元器件到格点处

    “Align”中的命令——

    “Align To Grid”:对齐到格点

    “Move All Components Origin To Grid ”:移动所有元器件到栅格点。

## PCB的规则设置

规则设置可以说是PCB设计过程中非常重要的一步，如果我们在设计之初就对规则进行了合理的设置，那它将非常有利于提高后期自动布线的效率和效果。

以AISkyLab-STM32F103CxT6.PrjPcb为例。在完成布局的PCB编辑器内，执行：“Design”-“Rules”,打开规则设置对话框。

![](media/9bcbc0be0d19be90f19b70330f883c14.png)

其中红线框内的为我们通常需要设置的一部分规则。这些规则如果设置不合适，在完成布线进行DRC检查时，通常会出现一堆错误，让新手不知所措。

这部分参数的设置，通常需要我们结合实际加工厂的制造工艺进行设置。比如下面总结了常用的几家厂家加工工艺说明：

1.  嘉立创工艺： <https://www.jlc.com/portal/vtechnology.html>

2.  华秋PCB工艺： <https://www.hqpcb.com/ability.html>

3.  捷多邦工艺： <https://www.jdbpcb.com/processshow/>

规则分类共有10个大类，在左侧的列表中，我们可以看到。

1.  

### “Electrical Rules(电气规则)”类：

这类规则主要针对具有电气特性的对象，用于系统的DRC（电气规则检查）功能。

![](media/a4c2ec3bbd1ee40da307e27a0f2956df.png)

1.  “Clearance”-安全间距规则：

    ![](media/a903f5133099251d66a32da23b94102a.png)

    这里可以设置导线，焊盘，过孔，铜箔等对象之间的间距。

    需要注意的是，我们可以为不同的对象设置不同的规则，这样就可以添加多条间距规则。

    在“Where the First objects matches”和“Where the Second objects
    matches”处设置规则适配的对象，在Constraints处设置规则的参数。

2.  “Short-Circuit”-短路规则：

    用于设置电路板上是否可以出现短路。通常我们使用默认的不允许即可。

3.  “Un-Routed Net”-不进行布线的规则：

    设置电路板上是否可以出现未连接的网络。通常设置不允许。但某些特殊的设置，不如使用
    外接的短路线或者跳线时可以允许，但最好设置针对的具体对象。

4.  “Un-Connected Pin”-未连接引脚的规则：

    当存在未布线的引脚时，会触发该规则的警告或报错。

5.  “Modified Polygon”-编辑的多边形区域：

    对编辑后的多边形覆铜区域的规则。

6.  “Creepage Distance”-爬电距离规则：

    设置爬电距离的参数规则。

### “Routing(布线规则)”类：

这些规则主要用于设置布线过程中的布线规则，如布线宽度，布线优先级，布线拓扑结构等8种布线规则。

![](media/180c95c2052b31a7fa960b80a6f0ee45.png)

1.  “Width(走线宽度规则)”：

2.  “Routing Topolgy(走线拓扑规则)”：

3.  “Routing Priority(布线优先级设置)”：

4.  “Routing Layers(布线层设置)”：

5.  “Routing Corners(布线拐角规则)”：

6.  “Routing Via Style(过孔样式规则)”：

7.  “Fantout Control(扇出规则)”：

8.  “Differential Pairs Routing(差分布线规则)”：

### “SMT(表面贴装规则)”类：

主要用于设置表面贴装元器件的走线规则。主要包括：

1.  “SMD To Corner”(SMD焊盘与导线拐角最小间距规则):

2.  “SMD To Plane”(SMD焊盘与中间层间距规则):

3.  “SMD Neck-Down”(SMD焊盘颈缩率规则):

4.  “SMD Entry”(SMD焊盘连接进入方向规则):

### “Mask(阻焊规则)”类：

主要用于阻焊层铺设的尺寸规则，主要用于Output
Gerneration(输出阶段)。系统提供了“Top Paste”(顶层锡膏保护层)、“Bottom
Paste”(顶层锡膏保护层)、”Top Solder”(顶层阻焊层)、”Bottom Solder”(底层阻焊层)

1.  Solder Mask Expansion

    ![](media/ce740ad98457ab38f9271855c57b16a5.png)

2.  Paste Mask Expansion

![](media/da315ef26a22eefc4fade36d12009c75.png)

### “Plane(内电层规则)”类：

主要用于设置中间电源层的走线与连接规则。

![](media/82d3597d5bfae9e3a5f394157d9ac75d.png)

“Power Plane Connect Style(电源层连接规则)”：

“Power Plane Clearance（电源层安全间距规则）”：

“Polygon Connect Style(焊盘与多边形覆铜区域的连接方式规则)”：

### “Testpoint(测试点规则)”类：

主要用于设置测试点布线规则，主要包括装配测试点和装配测试点使用规则。

![](media/fe1d3e67807c177dc448befa66bb35ed.png)

### “Manufacturing(生产制造规则)”类：

这里的规则需要根据PCB制作工艺来设置有关参数。主要用在在线DRC和批处理DRC执行过程中。主要有9种。

![](media/03b9b08e38ed6272dbbe72d1546dc4fe.png)

Minimum Annular Ring(最小环孔限制):

Acute Angle(锐角限制规则)：

Hole Size(钻孔尺寸规则)：

Layer Pairs(工作层对规则)：

Hole To Hole Clearance(钻孔间距规则)：

Minimum Solder Mask Sliver（最小阻焊条规则）：

Silk To Solder Mask Clearance(丝印与阻焊层间距规则)：

Silk To Silk Clearance(丝印间距规则)

Net Antennae(天线规则)：

Board Outline Clearance(电路板轮廓间隙)

### “High Speed(高速信号规则)”类：

该类规则主要用于设置高速信号布线规则，主要由6大类。

![](media/82076d17b3fc9c40a3d0d7fd2f5f19a7.png)

该部分内容将在后面结合高速布线的实例项目进行介绍。

### “Placement(放置规则)”类：

这部分规则主要用于设置元器件布局规则。一般只用在对元器件布局有严格要求的场合中使用。

![](media/0272a6d2ac0be005c8ce3fe5ea3ee306.png)

### “Signal Intergrity(信号完整性规则)”类：

这部分规则主要用于设置信号完整性要求的规则，比如：信号上升沿，信号下降沿，信号过冲约束等等。默认没有规则，需要根据项目要求手动创建。

![](media/32781c39c570625c406613de9661a28e.png)

## PCB的布线

布局和规则设置完成后，就可以进行PCB的布线了。我们可以借助软件的自动布线功能对要求不高的部分进行自动布线。对关键信号和重要信号以及其他特殊的走线进行手动布线。

1.  

### 自动布线

设置自动布线的策略，“Route”-“Setup”。

![](media/6cb31443f012bdc0950ecbe7044f765e.png)

弹出策略设置对话框：

![](media/fbd4545326581527ab3c4f65b91a3e59.png)

在“Routing
Strategies”中设置已有的或者添加新的自动布线策略。默认有5种布线策略可以选择。

点击“Add”可以添加自己定义的布线策略。如下图：

![](media/9f8325f8fd93f22c7b7050459ed557a4.png)

布线策略这只完成，就可以根据需要，进行自动布线。比如：全局自动布线，对指定网络进行，对网络类进行，对区域进行，对空间（Room）进行，对某个元件进行，对器件类进行，对选中的对象进行，选中对象之间的连接进行等。这些都依赖与良好的规则和布局。

比如本例，执行All后，软件会进行自动布线，并在“Message”中显示布线提示：

![](media/a9684e5249af577fe66236e979d90891.png)

### 手动布线

经过初步自动布线的电路，我们需要根据项目的特殊性，对电路板进行手动布局的优化。

手动布线需要多加练习和总结技巧，经常总结布线技巧，积累经验，能够在以后的项目中不断提高自己的布线水平。

1.  删除部分不够理想的布线。

    可以执行： “Route”-“Un-Route”-对应的取消布线的命令。

2.  手动布线：

    1.  放置交互式布线，光标变成十字形。（或者直接Ctrl + W）

    2.  移动光标到焊盘上，单击放置起点。多次单击放置不同的控制点，可以设置走线的方向。

        方向主要有：
        任意角度走线，90°拐角走线，90°圆弧角走线，45°拐角走线，45°圆弧角走线。

        按Tab可以在属性面板进行设置：

        ![](media/8a612893f1149b3970fb331254932ec2.png)

## 添加泪滴与覆铜

完成所有布线后，应进行泪滴添加和覆铜处理。

![](media/e1a69e4d11a285a5a95ac575c8976591.png)

泪滴的添加：

“Tools”-“Teardrops”,弹出泪滴参数设置对话框：

![](media/4a25beae9b6efb3a7f3fadd0ffbc6f4f.png)

点击“OK”，既可以执行添加泪滴。

泪滴添加完成后再进行覆铜处理。右击鼠标，“Place”-“Polygon Pour...”（快捷键P+G）

在需要的位置绘制多边形覆铜。

注意设置覆铜的属性：

![](media/3b8ad76dfa28f8be5547cd882023cf41.png)

在“Properties”中，应添加覆铜所属于的Net。

填充模式有三个按钮：
Solid(实体填充)、Hatched（网状填充）、None（外边框，内部中空）。

还要注意其中一个下拉列表中有：

![](media/11cf382b54b3837edf0af6aaf9a3a2ba.png)

我通常选择第二项：“Pour Over All Same Net Objects”。

而且，需要勾选去除死铜选项（Remove Dead Copper）。

## PCB的3D视图

我们设计PCB，进行布线时是在2维视图下操作的。但我们在设计过程中，可以随时切换到3D视图界面，查看电路板的3D仿真设计情况。只需要按键盘上的数字键3即可。（或者在菜单栏“View”-2D
Layout Mode/3D Layout Mode之间切换）

![](media/9004aff94c7f002df9800e9e986ade21.png)

如果要切换回2维视图，只需要按数字键2即可切换回2维布线编辑器。

## PCB的后期操作

PCB Layout布线工作完成后，后期主要进行检查，进行批处理DRC，生成报表。

1.  

2.  

3.  

### 对完成布线的PCB板进行DRC检查

在PCB编辑器内，“Tools”-“Design Rules
Check”,弹出对话框，默认会按照之前的设置规则进行检查。

![](media/8cbc5b606dfec7396f75bdb41477fd9b.png)

点击左下角，“Run Design Rule Check”，会生成Design Rule Verification
Report，如果有错误或者警告也会在Message面板显示。如果没有错误，Message面板则没有条目。

![](media/fc54062303060ecc74d1bebe573c840f.png)

### 生成电路板信息报表

在菜单栏“Reports”-“Board Infomation”,弹出设置对话框：

![](media/8db3c979ff1053076b03e30bc0d080ae.png)

选择需要的信息，点击打勾，点击Report就可以生成报告了。

![](media/adb528add1666a53a44892418635dc77.png)

也可以选择在PCB编辑器查看“Property”属性，其中有“Board Information”相关的信息。

![](media/d07635d4924295c0923ccc8cb415888d.png)

### 元器件报表

元器件报表是项目中使用的元器件信息的汇总表。

可以参考我的视频：《AD20自定义BOM模板一键生成BOM

》

配置能够自定义参数的元器件清单：

![](media/11ba83f3aa4d08a41155c494a6303fa9.png)

### 项目归档

项目归档时，按照步骤和文件类型。我个人总结了7个步骤：

S101-Gerber文件(包括钻孔文件)

S201-坐标文件

S202-物料清单

S301-固件

S401-3D文件

S501-原理图PDF文件

S601-源文件

所以，上述归档资料中，除了S301步骤的固件不在Altium
Designer中生成，其它都由Altium Designer批处理“Output Job File”生成。

“File”-“New”-“Output Job File”：

![](media/fea1bcc6dad7fcac5cf2333f4e87e0c9.png)

在这个文件中可以配置批处理脚本。主要类别有：

Netlist Outputs：网络表输出

Simulator Outputs:仿真输出

Documentation Outputs:文档类输出

Assembly Outputs:装配文件输出

Fabrication Outputs:加工文件输出

Report Outputs:报告文件输出

Validation Outputs:验证类文件输出

Export Outputs:导出第三方类文件输出

PostProcess Outputs:拷贝文件

这个文件非常好用，可以将所有批处理放在一个文件中，逐个执行。

也可以将每类输出单独放到一个输出配置文件中，按类执行。

而且这些文件一旦设置好后，可以直接复制到其他项目，添加到项目中略作修改就可以使用，非常方便。

这部分内容将在后期以单独一期视频的形式进行分享。
