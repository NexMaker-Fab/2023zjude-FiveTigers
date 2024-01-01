# 旋转机构

## Solidworks简介
SolidWorks 是一个流行的计算机辅助设计 (CAD) 和计算机辅助工程 (CAE) 软件，由 Dassault Systèmes 开发并发布。自1995年首次发布以来，它已成为机械设计、工程及其他领域的首选软件。SolidWorks 提供了一套全面的设计工具，可以进行 3D 建模、模拟、数据管理、产品数据管理等多种功能。

SolidWorks 的主要特点:
1. 直观的用户界面: 允许工程师和设计师轻松地创建复杂的3D模型。
2. 强大的模拟工具: 不仅可以进行基本的结构分析，还包括流体动力学、热分析等。
3. 数据管理: 提供了完整的产品数据管理 (PDM) 解决方案，方便团队协同工作。
4. 与其他Dassault Systèmes产品的集成: 如 CATIA、SIMULIA 等。

与 Fusion 360 的比较:
Fusion 360 是由 Autodesk 开发的 3D CAD、CAM 和 CAE 工具。与 SolidWorks 相比，Fusion 360 更倾向于为设计师、制造商和工程师提供一个集成的解决方案。
1. 云基础: Fusion 360 是基于云的，这意味着用户可以从任何地方访问他们的设计，而 SolidWorks 则是基于桌面的。
2. 价格: Fusion 360 通常比 SolidWorks 便宜，尤其对于小型企业和个人用户。
3. 功能: 虽然两者都是全功能的 CAD 系统，但 SolidWorks 在某些高级功能上可能具有更大的优势，尤其是在复杂的模拟和分析方面。
4. 易用性: Fusion 360 的界面被认为是更现代和直观的，尤其是对于初学者。
5. 集成的 CAM 工具: Fusion 360 内置了 CAM 工具，而 SolidWorks 需要额外的插件或软件。

总结: SolidWorks 和 Fusion 360 都是强大的设计工具，选择哪一个取决于特定的需求、预算和偏好。对于需要高级模拟和数据管理功能的大型企业，SolidWorks 可能更合适。而对于小型企业和个人用户，尤其是那些希望利用云计算和集成的 CAM 功能的用户，Fusion 360 可能是更好的选择。

## 基础设置

操作方式基础设置，进入首选项

![600](../project/_附件/Pasted%20image%2020240101110024.png)

调整快捷方式为soildworks,默认动态观察类型为受约束的动态观察，勾选反转缩放方式。这样操作起来更加顺手。

<img src="../img/../02/project/_附件/1.png" width=1920>

## 建模

最终效果
<iframe src="https://myqq45847.autodesk360.com/shares/public/SH512d4QTec90decfa6e298d9979e6627147?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

选择草图，确定放置的视角，放置草图

![600](../project/_附件/Pasted%20image%2020240101103738.png)

选择上方草图栏工具，绘制草图，点击完成草图则退出草图模式

![600](../project/_附件/Pasted%20image%2020240101103858.png)

建立草图约束，实现草图关系更好的位置调整

![600](../project/_附件/Pasted%20image%2020240101104037.png)

建立约束关系后，小长方形的尺寸能够在大长方形上进行自由调整长度。

![600](../project/_附件/Pasted%20image%2020240101104403.png)

另一种动态关系约束，小长方形能够随着大长方形的尺寸改变而改变。

<img src="../img/../02/project/_附件/Pasted%20image%2020240101104626.png" width=1920>

找到需要调整的参数，双击重命名进行修改，更加醒目

<img src="../img/../02/project/_附件/Pasted%20image%2020240101104835.png" width=1920>

建立联动表达式关系

![600](../project/_附件/Pasted%20image%2020240101105342.png)

联动修改

![600](../project/_附件/Pasted%20image%2020240101105543.png)

通过旋转，由草图建立出圆柱

![600](../project/_附件/Pasted%20image%2020240101110512.png)

通过拉升指令，得到形体

![600](../project/_附件/Pasted%20image%2020240101110814.png)

move to create a replica

![600](../project/_附件/Pasted%20image%2020240101111003.png)

Similarly, a cylinder is obtained by symmetric stretching, and the cylinder is changed to have the sketch plane as the center of symmetry

![600](../project/_附件/Pasted%20image%2020240101111359.png)

Perform Boolean subtraction

![600](../project/_附件/Pasted%20image%2020240101111646.png)

Boolean subtraction yields a concatenated slot that facilitates subsequent rotation

![600](../project/_附件/Pasted%20image%2020240101111749.png)

Repeat the steps above to obtain the following shape

![600](../project/_附件/Pasted%20image%2020240101111924.png)

偏移构造镜像平面

![600](../project/_附件/Pasted%20image%2020240101142408.png)

镜像

![600](../project/_附件/Pasted%20image%2020240101145057.png)

与此前同样的方法构建出整体

![600](../project/_附件/Pasted%20image%2020240101145159.png)

连接位置生成式设计

<video src="../img/../02/project/_附件/11.mp4" width="1080px" height="500px" controls="controls"></video>

生成式结构

![600](../project/_附件/Pasted%20image%2020240101145608.png)

构建固定连接环

![600](../project/_附件/Pasted%20image%2020240101145535.png)

固定杆生成式设计

<video src="../img/../02/project/_附件/自动化建模2.mp4" width="1080px" height="500px" controls="controls"></video>

造型搭建完成

![600](../project/_附件/Pasted%20image%2020240101151455.png)

## voronoi插件
下载voronoi插件
在脚本中心下载安装Voronoi sketch Generator脚本：[https://apps.autodesk.com/FUSION/en/Detail/Index?id=1006119760063675415&os=Win64&appLang=en](https://apps.autodesk.com/FUSION/en/Detail/Index?id=1006119760063675415&os=Win64&appLang=en)，下载后依次默认安装即可。

![600](../project/_附件/Pasted%20image%2020240101155429.png)

重启fusion360,出现Voronoi sketch Generator则安装成功

![600](../project/_附件/Pasted%20image%2020240101155323.png)

确定需要进行voronoi的区域，尺寸为20* 6 

![600](../project/_附件/Pasted%20image%2020240101152139.png)

启用Voronoi sketch Generator插件，选择目标平面所在的平面以及上述的尺寸

![600](../project/_附件/Pasted%20image%2020240101153715.png)

选择不同的效果

![600](../project/_附件/Pasted%20image%2020240101152845.png)

不同效果的尝试

![600](../project/_附件/Pasted%20image%2020240101153016.png)

确定好最终的样式，点击导入到fusion360中

![600](../project/_附件/Pasted%20image%2020240101153104.png)

得到一个具有voronoi的草图平面

将该平面移动缩放到目标位置

选取草图对象为目标，然后设置移动的轴心，

![600](../project/_附件/Pasted%20image%2020240101154056.png)

得到图示的草图

![600](../project/_附件/Pasted%20image%2020240101154209.png)

将草图进行拉伸剪切操作

![600](../project/_附件/Pasted%20image%2020240101154320.png)

得到最终的造型

![600](../project/_附件/Pasted%20image%2020240101154444.png)

对另一侧也进行同样的操作

![600](../project/_附件/Pasted%20image%2020240101154750.png)



## 创建零部件连接关系

从实体创建零部件

<img src="../img/../02/project/_附件/Pasted%20image%2020240101151617.png" width=1920>

将零部件命名好对应的名称

<img src="../img/../02/project/_附件/Pasted%20image%2020240101151705.png" width=1920>

将需要固定的零件选择固定进行固定

<img src="../img/../02/project/_附件/Pasted%20image%2020240101151705.png" width=1920>


将需要固定的零件进行固定

![600](../project/_附件/Pasted%20image%2020240101155600.png)

对关节位置进行旋转连接装配

![600](../project/_附件/Pasted%20image%2020240101155823.png)

根据需求依次同上述方法进行装配

![600](../project/_附件/Pasted%20image%2020240101155930.png)

为了更好的观察旋转效果，在上方挖出两个槽口

![600](../project/_附件/Pasted%20image%2020240101160111.png)

旋转效果演示

<video src="../img/../02/project/_附件/1月1日.mp4" width="1080px" height="500px" controls="controls"></video>

## Engineering Drawings

选择零部件进行导出

![600](../project/_附件/Pasted%20image%2020240101162129.png)

在新的设计中打开该零件并进入工程图模式

![600](../project/_附件/Pasted%20image%2020240101162225.png)

注意旋转零件与坐标轴平行

![600](../project/_附件/Pasted%20image%2020240101164854.png)

选择对应的相关参数

<img src="../img/../02/project/_附件/Pasted%20image%2020240101162312.png" width=1920>

在创建-基础视图中, select the proper orientation and style.

<img src="../img/../02/project/_附件/Pasted%20image%2020240101162526.png)" width=1920>

保持缩放比例尺，旋转找到合适的位置

![600](../project/_附件/Pasted%20image%2020240101165114.png)


标注出尺寸，添加技术要求

![600](../project/_附件/Pasted%20image%2020240101165939.png)

左上角标注缩放比例，右下角标注相关零件信息导出图纸

![600](../project/_附件/Pasted%20image%2020240101170057.png)

![600](../project/_附件/Pasted%20image%2020240101170127.png)

## 网页端模型展示

在文件-web中跳转网页页面

![600](../project/_附件/Pasted%20image%2020240101170724.png)

在网页端，视图中查看网页模型

![600](../project/_附件/Pasted%20image%2020240101170952.png)

在共享-嵌入中找到网页嵌入代码，进行嵌入预览

![600](../project/_附件/Pasted%20image%2020240101171049.png)


