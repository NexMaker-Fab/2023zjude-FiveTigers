# APP

## 预览效果

<video src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/1.mp4" width="1025px" height="500px" controls="controls"></video>

<video src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/sparkle.mp4" width="1025px" height="500px" controls="controls"></video>

## 所需工具

1. Processing 4.3 [官方安装页面](https://processing.org/)
   
2. Android Studio [官方安装页面](https://developer.android.com/studio?hl=zh-cn)
   
3. 一条数据线和一部安卓手机

## 安装Android Studio并部署环境

Android Studio安装方法：[B站视频](https://www.bilibili.com/video/BV19U4y1R7zV?p=4&vd_source=de4f37c2f89f0135a4c4623934ad39b7)

启动Android Studio，创建新项目，选择 Empty Views Activity模板

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled.png)

为项目选择路径并命名，注意选择Java语言，点击Finish

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%201.png)

## Gradle

### 什么是Gradle
Gradle 是一个流行的构建工具，用于自动化构建、编译、测试和部署软件项目。它是一个基于 Groovy 和 Kotlin 的构建工具，用于管理项目的依赖关系和构建过程，能够帮助开发者自动化项目的构建流程，提高开发效率，并简化安卓项目管理和维护。

### Gradle的作用
1. 项目构建： Gradle 允许你定义项目的结构和构建过程。通过编写简洁的构建脚本，你可以指定项目的依赖关系、任务以及如何构建和打包项目。

2. 依赖管理： Gradle 支持管理项目所需的外部依赖。它能够轻松地配置和下载库、框架和其他软件包，并将它们集成到项目中。

3. 多项目构建： Gradle 支持构建多模块的项目。它可以管理多个相关项目的构建，简化了整体项目结构的管理和维护。

4. 任务管理： 你可以定义各种任务来执行特定的操作，比如编译代码、运行测试、生成文档、打包发布等。

5. 插件扩展： Gradle 允许用户编写自定义插件或使用现有插件，以扩展其功能。这些插件能够简化构建过程，提高开发效率。

6. 多语言支持： Gradle 不仅支持 Java，还支持其他语言，如 Kotlin、Groovy、Scala 和 C++ 等，使其成为一个通用的构建工具。
   
### 下载Gradle

一般情况下，Android Studio会自动下载Gradle，如果因为网络等原因无法下载，可以开启VPN或参考这篇文章：[CSDN教程](https://blog.csdn.net/Jia_Feng_/article/details/115268372)

本项目所使用的的gradle版本和文件路径

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%202.png)

## 创建模拟器

如果你使用的是苹果手机，手头上没有安卓手机，可以在Android Studio中创建安卓系统的模拟器来代替手机。

在Android Studio右侧，点击Device Manager，之后点击Create Device按钮。

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%203.png" width=1080>

选择使用的手机类型，这里选择的是Pixel 2，然后点击Next。

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%204.png)

选择Android 设备的操作系统镜像，选择合适的 System Image 对于模拟器的性能和功能非常重要。不同的镜像版本可能具有不同的功能和特性，比如新的 API、更新的系统级别功能等。这里选择R。

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%205.png)

确认所选的参数，为模拟器命名，点击Finish。

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%206.png)

在Device Manager的Actions中选择需要启动的模拟器即可。

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%207.png" width=1080>

## 下载并导入所需库文件

本项目除了Android Studio中自带的库文件之外还需要两个额外的库文件：

1. processing.core：[Github](https://github.com/processing/processing-android/releases)

注意将processing-core.zip的后缀改成.jar。

2. Ketai：[Ketai offical website](http://ketai.org/download/)

解压并将 `processing-core.jar` 和 `Ketai.jar` 复制到 项目文件/app/libs 这个路径下。

**在Android Studio中导入库文件：**

点击设置，选择Project Structure

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%208.png" width=1080>

选择Dependencies，选择app，点击Declared Dependencies下的 + ，选择JAR/AAR Dependency

![Untitled](APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%209.png)

输入库文件的绝对路径，点击OK即可

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2010.png" width=1080>

对另外一个文件执行相同的操作。

## 代码文件

打开Android窗口，切换到Android视图

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2011.png" width=1080>

在该位置创建 Sketch.java 文件，要求名称完全一致

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2012.png" width=1080>

复制以下代码到Sketch.java中：

```java

package com.example.helloworld;

import processing.core.PApplet;
import processing.core.PVector;

import java.util.ArrayList;
import java.util.Iterator;

import ketai.camera.*;


public class Sketch extends PApplet {
  int width = 1440;
  int height = 3200;

  KetaiCamera cam;

  public class Particle {
    public PVector acc = new PVector(0, 0);
    private float damping = 0.5F; // 阻尼系数
    public PVector pos;
    public PVector vel;
    public float size_;
    public int[] color_;

// 构造函数，用于初始化粒子的位置、速度、规模和颜色

    public Particle(PVector pos_, PVector vel_, float size_, int[] color_) {
      this.pos = pos_;//粒子位置
      this.vel = vel_;//粒子速度
      this.size_ = size_;//粒子规模
      this.color_ = color_;
    }

// 应用加速度的方法

    public void applyAcc(PVector acc_) {
      this.acc.add(acc_); //add() 方法是用于将两个向量相加的方法，应用加速度
    }

    // 更新粒子状态的方法

    public void update() {
      this.vel.add(this.acc);
      this.pos.add(this.vel);
      this.acc.mult(this.damping); // 衰减
    }

    // 在画布上绘制粒子的方法

    public void show() {
      stroke(this.color_[0], this.color_[1], this.color_[2]);
      strokeWeight(this.size_);
      point(this.pos.x, this.pos.y); //绘制一个点，即一个像素维度的空间坐标。第一个参数是点的水平值，第二个值是点的垂直值，可选的第三个值是深度值。
    }


  }


  public class Firework extends Particle {
    // 继承的属性
    private float damping = 0.8F; // 阻尼系数
    private PVector Gravity = new PVector(0, 0.001F); //重力向量
    private boolean Explode = false; //是否爆炸
    private float MaxVelocity = 8; // 调整弹道速度，最大速度

    // 构造函数
    public Firework(PVector pos_, PVector vel_, float size_, int[] color_) {
      super(pos_, vel_, size_, color_); // 调用父类构造函数
    }

    // 更新方法
    public void update() {
      if (!Explode) {
        // 在爆炸前，调整速度朝向鼠标位置
        PVector target = new PVector(mouseX, mouseY);
        PVector acc = PVector.sub(target, pos).normalize().mult(0.3F);//0.1经过光标时爆炸延迟
        applyAcc(acc);
      } else {
        applyAcc(Gravity);
      }
      vel.limit(MaxVelocity);

      vel.add(acc);
      pos.add(vel);
      acc.mult(damping);  // 衰减
    }

    // 显示方法
    public void show() {
      if (vel.y < 1) {// 弹丸爆炸前的消失速度
        float alpha_ = -vel.y * 20; // 不透明度：0不可见【逐渐消失效果】
        stroke(color_[0], color_[1], color_[2], alpha_);//描边
        strokeWeight(size_);

        point(pos.x, pos.y);

      } else {
        Explode = true;
      }
    }
  }


  public class fireworks {
    private final PVector Gravity = new PVector(0, 0.008F);//改变爆炸后的重力加速度
    private int lifeT = 600; //生命周期
    private Particle[] fs;
    private PVector pos;
    private int[] color_;
    private int N;

    public fireworks(PVector pos_, int[] color_, int N_) {
      this.pos = pos_;
      this.color_ = color_;
      this.N = N_;
      this.fs = new Particle[N];

      for (int i = 0; i < N; i++) {
        PVector particlePos = new PVector(this.pos.x, this.pos.y);
        float V = random(2, 8);//调整爆炸后的粒子速度，影响爆炸形状
        PVector vel_ = PVector.random2D().mult(V);
        float size_ = 3;//控制爆炸后粒子大小
        int[] particleColor = {this.color_[0], this.color_[1], this.color_[2]};
        Particle f = new Particle(particlePos, vel_, size_, particleColor);
        this.fs[i] = f;
      }
    }

    public void update() {
      for (Particle f : this.fs) {
        f.applyAcc(Gravity);
        f.update();
      }
    }

    public void show() {
      this.lifeT -= 1;
      if (this.lifeT > 0) {
        for (Particle f : this.fs) {
          int alpha_ = this.lifeT * 11; // 不透明度：0不可见
          stroke(f.color_[0], f.color_[1], f.color_[2], alpha_);
          strokeWeight(f.size_);
          point(f.pos.x, f.pos.y);
        }
      }
    }
  }

  PVector pos_ = new PVector(random(width / 3, 2 * width / 3), height / 2);//疑似没啥用
  int[] color_ = {(int) random(150), (int) random(10), (int) random(150)};//烟花颜色
  fireworks f = new fireworks(pos_,color_,(int)random(100,400));
  ArrayList<Firework> ps = new ArrayList<>();
  ArrayList<fireworks> fs = new ArrayList<>();
  int N =12;
  int size_=10;

  public void settings() {
    fullScreen(P3D);
    fs.add(f);
    size(height,width);
    noSmooth();//禁用图形的平滑处理（anti-aliasing），从而使图形显示更为锐利
  }

  public void setup(){
    orientation(PORTRAIT);//纵向屏幕
    cam = new KetaiCamera(this, height, width, 30);                 // 1
    cam.start();
    imageMode(CENTER);
  }

  public void draw(){
    //fill(0,61);
    //noStroke();
    //rect(0,0,width,height);

    if (cam.isStarted()) {
      cam.read();
      pushMatrix();
      translate(width/2,height/2);
      rotate(HALF_PI);
      image(cam, -width/2, 0,height,width);
      popMatrix();
    }





    //鼠标指示
    fill(0, 255, 0);
    ellipse(mouseX, mouseY, 20, 20);
    int[] color_ = {(int) random(255), (int) random(255), (int) random(255)};//烟花颜色

    //更新ps数组
    if((random(1)<0.1)&&(ps.size()<10))
    {

      pos_ = new PVector(random(0,width),height);//发射位置
      PVector vel_ =new PVector(random(20F,50F),random(-45,-30));//爆炸后的速度
      Firework p = new Firework(pos_,vel_,size_,color_);
      ps.add(p);
    }

    Iterator<Firework> iterator = ps.iterator();
    while (iterator.hasNext()) {
      Firework p = iterator.next();
      p.update();
      p.show();
      if (p.Explode) {
        pos_ = p.pos;
        color_ = p.color_;
        f = new fireworks(pos_, color_, 300);//300:粒子数量
        fs.add(f);
        if (fs.size() >= 20) {
          fs.remove(0);
        }
        iterator.remove(); // 使用迭代器的 remove 方法安全地删除元素
        tint(255, 101);
      }

      for (fireworks f : fs){
        f.update();
        f.show();
      }


    }
  }
  void onCameraPreviewEvent() {                                 // 4
    cam.read();                                                 // 5
  }


}


```

打开MainActivity.java

复制以下代码到MainActivity.java中：

```java

package com.example.helloworld;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.ViewGroup;
import android.widget.FrameLayout;
import processing.android.PFragment;
import processing.android.CompatUtils;
import processing.core.PApplet;

public class MainActivity extends AppCompatActivity {
    private PApplet sketch;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        FrameLayout frame = new FrameLayout(this);
        frame.setId(CompatUtils.getUniqueViewId());
        setContentView(frame, new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,
                ViewGroup.LayoutParams.MATCH_PARENT));

        sketch = new Sketch();
        PFragment fragment = new PFragment(sketch);
        fragment.setView(frame, this);
    }

    @Override
    public void onRequestPermissionsResult(int requestCode, String permissions[], int[] grantResults) {
        if (sketch != null) {
            sketch.onRequestPermissionsResult(
                    requestCode, permissions, grantResults);
        }
    }

    @Override
    public void onNewIntent(Intent intent) {
        super.onNewIntent(intent);
        if (sketch != null) {
            sketch.onNewIntent(intent);
        }
    }
}

```

打开AndroidManifest.xml

复制以下代码到AndroidManifest.xml中：

```xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" package="com.example.helloworld">
    <uses-permission android:name="android.permission.CAMERA"
        tools:ignore="PermissionImpliesUnsupportedChromeOsHardware" />
    <uses-permission android:name="android.permission.BLUETOOTH"/>
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>


    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Helloworld"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```

## 预览应用

手机打开开发者选项，允许USB调试，允许USB下载应用，连接电脑
[CSDN开启安卓设备开发者模式](https://blog.csdn.net/weixin_40883833/article/details/131258378)

将手机和电脑使用USB线连接，在Android Studio上方找到对应的手机型号。

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2013.png" width=1080>

点击右侧的运行，在手机上预览效果。

## 导出APK安装包

点击Build-Generate Signed Bundle / APK

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2014.png" width=1080>

选择APK，点击Next

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2015.png" width=1080>

如果没有密钥，请创建密钥：[https://blog.csdn.net/tzhenxiong/article/details/109901468](https://blog.csdn.net/tzhenxiong/article/details/109901468)

选择密钥的路径并输入密码，点击Next

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2016.png" width=1080>

选择release，点击Create

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2017.png" width=1080>

默认的应用文件位置，名称为app-release.apk：

<img src="fin/APP%2010e3940a07584e41a39350b122b2d6b7/Untitled%2018.png" width=1080>