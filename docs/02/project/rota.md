# 旋转机构

## 基础设置

操作方式基础设置，进入首选项

![600](../project/_附件/Pasted%20image%2020240101110024.png)

调整快捷方式为soildworks,默认动态观察类型为受约束的动态观察，勾选反转缩放方式。这样操作起来更加顺手。

<img src="02/project/_附件/1.png" width=1920>

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

<img src="02/project/_附件/Pasted%20image%2020240101104626.png" width=1920>

找到需要调整的参数，双击重命名进行修改，更加醒目

<img src="02/project/_附件/Pasted%20image%2020240101104835.png" width=1920>

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

<video src="02/project/_附件/11.mp4" width="1080px" height="500px" controls="controls"></video>

生成式结构

![600](../project/_附件/Pasted%20image%2020240101145608.png)

构建固定连接环

![600](../project/_附件/Pasted%20image%2020240101145535.png)

固定杆生成式设计

<video src="02/project/_附件/自动化建模2.mp4" width="1080px" height="500px" controls="controls"></video>

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

<img src="02/project/_附件/Pasted%20image%2020240101151617.png" width=1920>

将零部件命名好对应的名称

<img src="02/project/_附件/Pasted%20image%2020240101151705.png" width=1920>

将需要固定的零件选择固定进行固定

<img src="02/project/_附件/Pasted%20image%2020240101151705.png" width=1920>


将需要固定的零件进行固定

![600](../project/_附件/Pasted%20image%2020240101155600.png)

对关节位置进行旋转连接装配

![600](../project/_附件/Pasted%20image%2020240101155823.png)

根据需求依次同上述方法进行装配

![600](../project/_附件/Pasted%20image%2020240101155930.png)

为了更好的观察旋转效果，在上方挖出两个槽口

![600](../project/_附件/Pasted%20image%2020240101160111.png)

旋转效果演示

<video src="02/project/_附件/1月1日.mp4" width="1080px" height="500px" controls="controls"></video>

## Engineering Drawings

选择零部件进行导出

![600](../project/_附件/Pasted%20image%2020240101162129.png)

在新的设计中打开该零件并进入工程图模式

![600](../project/_附件/Pasted%20image%2020240101162225.png)

注意旋转零件与坐标轴平行

![600](../project/_附件/Pasted%20image%2020240101164854.png)

选择对应的相关参数

<img src="02/project/_附件/Pasted%20image%2020240101162312.png" width=1920>

在创建-基础视图中, select the proper orientation and style.

<img src="02/project/_附件/Pasted%20image%2020240101162526.png)" width=1920>

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


