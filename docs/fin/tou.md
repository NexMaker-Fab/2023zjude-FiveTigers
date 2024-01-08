# Touchdesigner端

arduino代码调整，能够实现：读取mpu6050的x方向与y方向，以及按钮按下的状态。同时联通蓝牙，进行蓝牙通讯，最终通过touchdesigner端接受到蓝牙串口信号，进行后续工作。

进行相关的串口设置，使用了arduino nano type-c口，Processor选择328P。

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled.png" width=1080>

代码如下，将其上传至Arduino

```c
#include <Wire.h>
#include <MPU6050.h>
#include <SoftwareSerial.h>  // 软件串口库

MPU6050 mpu;
SoftwareSerial btSerial(10, 11); // RX, TX  定义蓝牙模块的软件串口，连接到数字10（HC-06 TX）和11（HC-06 RX）
const int buttonPin = 2; // 按钮连接的针脚

void setup() {
  Wire.begin();
  Serial.begin(9600);
  btSerial.begin(9600); // 初始化蓝牙模块串口通信的波特率
  mpu.initialize();
  pinMode(buttonPin, INPUT_PULLUP); // 设置按钮针脚为输入，并启用内部上拉电阻
  if (!mpu.testConnection()) {
    Serial.println("MPU6050 connection failed. Please check your connection.");
    while (1);
  }
}

void loop() {
  int16_t ax, ay, az;
  mpu.getAcceleration(&ax, &ay, &az);
  
  // 读取按钮状态
  int buttonState = digitalRead(buttonPin); // 读取按钮状态

  // 发送加速度数据和按钮状态到串口监视器
  Serial.print(ax);
  Serial.print(",");
  Serial.print(ay);
  Serial.print(",");
  Serial.println(buttonState == LOW ? "0" : "1"); // 按钮被按下时输出1，否则输出0
  
  // 同样发送加速度数据和按钮状态到蓝牙模块
  btSerial.print(ax);
  btSerial.print(",");
  btSerial.print(ay);
  btSerial.print(",");
  btSerial.println(buttonState == LOW ? "0" : "1"); // 按钮被按下时输出1，否则输出0
  
  delay(100);
}
```

实物接线图：

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%201.png)

串口数据正常

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%202.png)

通过蓝牙HC-06连接电脑，在蓝牙设置中进行如图所示的设置

![Graphein_2024-01-07_21-08-00.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-07_21-08-00.png)

连接未知的蓝牙设备

![Graphein_2024-01-07_21-09-02.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-07_21-09-02.png)

记住其串口号

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-07_21-09-29.png" width=1080>

打开xcom或其他串口调试助手，进行蓝牙通讯效果检测。

输入对应的上方窗口18，输入默认密码，一般为1234，

![Graphein_2024-01-07_21-10-22.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-07_21-10-22.png)

连接成功后得到提示

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-07_21-10-40.png" width=1080>

蓝牙通讯检测完毕，能够正常通讯。未防止串口占用，在检测完后需要断开串口。

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%203.png" width=1080>

## touchdesigner端烟花效果实现

### 1. 使用serial dat接入HC-06的串口数据

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%204.png)

完成屏幕相关的位置转换与映射，得到传感器对应的x,y在窗口中的位置。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%205.png)

完成按键部分的数据映射

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%206.png)

### 2. 烟花棒跟随模式

建立单一网格，映射检测到的位置坐标

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%207.png)

采用particle建立对应的粒子效果模块，具体的数值，需要根据实际情况调整。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%208.png)

采用4件套，将烟花棒跟随进行渲染呈现（如下图红框），采用blur,feedback,level，增强视觉呈现效果（如下图绿框所示）

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%209.png)

在add中预览效果

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2010.png" width=1080>

得到效果如视频所示,视频1.mp4

<video src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/视频1.mp4" width="1025px" height="500px" controls="controls"></video>

### 2. 放烟花模式

建立球体，映射坐标，模式为Ramdom,通过particle建立爆炸的粒子效果

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2011.png)

具体为控制点的位置沿法相方向移动

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2012.png)

参数如下，需要更具实际情况进行调整

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2013.png)

建立一个lfo波，连接math,数据控制映射范围为0-10000，，将math得到的数据连接到Birth中，控制烟花炸开的粒子数目，以及形成周期性的短暂炸开效果

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2014.png)

由于烟花爆炸还需要烟花升空的过程，也采用同样的方式进行处理，不同点在于采用单一网格的方式进行发射粒子以及需要一个额外的引导力，去引导发射方向，采用force模块。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2015.png)

将烟花球与烟花粒子飞升模块采用merge模块融合

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2016.png)

融合后连接跟随模式中同样的四件套模块，实现，炸开的烟花效果。

得到效果如视频所示,视频2.mp4

<video src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/视频2.mp4" width="1025px" height="500px" controls="controls"></video>

### 3. 随机平面字烟花呈现

在grasshopper中创建字的文件，同时统一尺寸在xyz在-10到10中，尝试不同的字体

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2017.png)

导出模型为obj,导入到touchdesigner中，

![Graphein_2024-01-08_13-28-44.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-08_13-28-44.png)

使用randomGenerator模块，得到一个0-4的随机数，且8s更新一次，通过随机数控制switch模块，随机选取出一个文字模型

![Graphein_2024-01-08_13-29-45.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-08_13-29-45.png)

采用transform模块实现位置映射与变形。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2018.png)

同前面的案例采用particle控制粒子实现烟花效果。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2019.png)

merge上烟花孢子上升的模块，融合后连接跟随模式中同样的四件套模块，实现，炸开的烟花效果。

得到效果如视频所示,视频3.mp4

<video src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/视频3.mp4" width="1025px" height="500px" controls="controls"></video>

### 4. 立体模型烟花呈现

选取建立出合适的模型，通过rhino重拓补功能进行减面处理（防止touchdesigner卡死）

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2020.png)

将模型放置在原点，同时控制尺寸大小比较想接近。

![Graphein_2024-01-08_02-26-10.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-08_02-26-10.png)

处理后的文件同前面文字处理方式为obj,将obj置入touchdesigner中，通过随机数进行选取。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2021.png)

为了凸显出立体模型的不同角度，以及不同的视觉冲击程度，采用RandomGenerator控制尺寸映射与角度映射

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2022.png)

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2023.png)

将模型粒子化以及通过force模块控制炸开的力效果。同时merge上烟花孢子上升的模块。融合后连接跟随模式中同样的四件套模块，实现，炸开的烟花效果。

得到效果如视频所示,视频4.mp4

<video src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/视频4.mp4" width="1025px" height="500px" controls="controls"></video>

### 5. 模式的切换

将上述的4种烟花效果模式，采用switch进行连接，通过前面得到的传感器按钮数据，进行模式切换。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2024.png)

### 6. 手机摄像头画面的获取

在[https://www.e2esoft.com/ivcam/](https://www.e2esoft.com/ivcam/)下载ivcam软件，用于电脑段接收手机摄像头画面，默认安装即可

<img src="fin/touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2025.png" width=1080>

安装完成后手机端也同样访问上述网址安装手机端。

手机端与电脑端同时打开，且保持在同一网络环境下，进行连接。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled.jpeg)

ivcom应用内连接成功

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2026.png)

在TD中用videodevin连接外部设想头设备，然后再叠加add1,合成画面add2

![Graphein_2024-01-08_13-48-45.png](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Graphein_2024-01-08_13-48-45.png)

在add2中查看最终的效果。

### 7. 手机端查看实时画面。

采用[https://letsview.cn/](https://letsview.cn/)下载****幕连，同****ivcam进行安装以及处于同一网络下进行连接。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%2027.png)

将add2进行全屏显示，手机接收画面。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%201.jpeg)

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%202.jpeg)

或采用腾讯会议进行屏幕共享。

![Untitled](touchdesigner%E7%AB%AF%20971b79550a73401591f45a70e640be3d/Untitled%203.jpeg)
