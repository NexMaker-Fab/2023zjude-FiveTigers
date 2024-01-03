# Shy flower

In this group project, the interaction between the user and the button determines the size of the flower, The longer you press the button, the more shy the flower will be, and the smaller the petals will be.

## Presentation

<img src="img/IAP/f1.gif" width=1080>

## Code
### Processing side:

```java

import processing.serial.*;
Serial port;

int num; //花瓣的数量
int angle = 30; //花瓣的角度
int radius1 = 150;  //控制花的大小
int radius2 = 200;  //控制花的大小
int velocity = 0; //花瓣运动速度


int a = 100;
int b = 300;
void setup(){
  fullScreen();  //满屏显示
  background(255, 255, 100);  //设置背景色为黄色
  stroke(128, 0, 128); //设置线条颜色为紫色
  num = (int)360/angle;  //计算花瓣数目,保证为整数
  port = new Serial(this,"COM5",115200);
}

int haha = 255;

void draw()
{
  fill(haha, haha, 100, 50);  
  rect(0, 0, width, height);
  translate(width/2, height/2);  //将坐标原点放在正中

  for (int i = 0; i < num; i++) {
    //利用三角函数，根据角度确定x y的坐标
    float x1 = sin(radians(i * angle + velocity)) * radius1;   //将角度改为弧度制进行计算
    float y1 = cos(radians(i * angle + velocity)) * radius1;
    float x2 = sin(radians(i * angle - velocity)) * radius2;   //(x2,y2)与(x1,y1)差一个花瓣角度
    float y2 = cos(radians(i * angle - velocity)) * radius2;
    //绘制贝茨曲线
    noFill();  //不填充
    bezier(x1, y1, x1+x2, y1+y2, x2+x1, y2+y1, x2, y2);  //绘制上花瓣
    bezier(x1, y1, x1-x2, y1-y2, x2-x1, y2-y1, x2, y2);  //绘制下花瓣

    //绘制控制点，方便观察
    fill(128, 0, 128); //给控制点上色
    //ellipse(x1, y1, 6, 6);
    //ellipse(x2, y2, 6, 6);
    ellipse(x1+x2, y1+y2, 6, 6); 
    //ellipse(x1-x2, y1-y2, 6, 6);
    //ellipse(x2-x1, y2-y1, 6, 6);
  }
  velocity += 1; //速度每次增加1
  
    char input = port.readChar(); //read information from Arduino 
    System.out.println(input);
    if(input == 'a'){
       
      radius1 -= 100;
      radius2 -= 100;
      haha = haha-20;
      
    }
    
    if(input == 'b'){
       
      radius1 += 20;
      radius2 += 20;
      haha = haha+20;
      
    }
    
    
    

}

```

### Arduino Side:

```c
int upPin = 3;

void setup() {
  pinMode(upPin,INPUT_PULLUP);

  Serial.begin(115200);  
}

void loop() {

  int up1 = digitalRead(upPin);

  if(up1 == 0)
  {
    Serial.write("a");
    delay(10);
  }

    if(up1 == 1)
  {
    Serial.write("b");
    delay(10);
  }
}


```

## Wiring Method

<img src="img/IAP/f2.png" width=1080>