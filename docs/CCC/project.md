# 激光切割加工实践

## 速度与功率的调整以及切割实践

1. **切割9个方形回路**：固定速度为30mm/s，最大功率依次从10%递增到90%，最小功率始终比最大功率小10%。

<img src="img/ccc/1%20(4).jpg" width=1920>

2. **机器启动检查**

<img src="img/ccc/1%20(1).jpg" width=1920>

3. **调整切割起始位置**

<img src="img/ccc/1%20(2).jpg" width=1920>

4. **切割结果**

<img src="img/ccc/1%20(3).jpg" width=1920>

## 使用激光切割加工小组LOGO

1. **图纸设计**：包括底座组件和LOGO旋转徽标。底座组件采用孔嵌合方式连接，底座的文字部分采用激光扫描，其他部分采用激光切割。徽标分为两层，第一层将主体形象镂空，第二层为透明亚克力板，与第一层黏合。

<img src="img/ccc/2%20(1).png" width=1920>

2. **参数调整**：激光切割的参数为速度5mm/s，最大功率100%，最小功率90%；激光扫描的参数为速度500mm/s，最大功率15%，最小功率5%。

<img src="img/ccc/2%20(1).jpg" width=1920>

3. **调整切割起始位置**

<img src="img/ccc/2%20(2).jpg" width=1920>

4. **切割过程**

<video src="img/ccc/1.mp4" width="1080px" height="500px" controls="controls"></video>

1. **切割结果**

<img src="img/ccc/3%20(2).jpg" width=1920>

<img src="img/ccc/3%20(1).jpg" width=1920>

<img src="img/ccc/3%20(3).jpg" width=1920>

<img src="img/ccc/3%20(4).jpg" width=1920>

## 激光切割零件组装

1. **安装底座**

<img src="img/ccc/image.jpg" width=1920>

2. **安装固定柱**

<img src="img/ccc/image%20(1).jpg" width=1920>

3. **安装徽标**：使用502速干胶水连接。

<img src="img/ccc/image%20(2).jpg" width=1920>

4. **组合效果**

<img src="img/ccc/image%20(3).jpg" width=1920>

## 与Arduino结合

1. **硬件结合**：使用舵机实现徽标的旋转效果。

<img src="img/ccc/21.jpg" width=1920>

<img src="img/ccc/22.jpg" width=1920>

2. **Arduino代码**
   
<img src="img/ccc/image%20(3).png" width=1920>

3. **最终效果**

<video src="img/ccc/2.mp4" width="1080px" height="500px" controls="controls"></video>