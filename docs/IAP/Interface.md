# Interface application programming

To connect the interface application programming in processing. Interface application programming in processing allows users to create interactive and visual applications by using a combination of programming and graphical interface tools. It provides a way for users to interact with their programs through buttons, sliders, and other graphical elements, making it easier to create dynamic and engaging applications. Interface application programming in processing also allows for the integration of external devices, such as sensors or cameras, to further enhance the interactivity of the applications. 

## Communication Between Processing and Arduino

### Arduino Side:

```c
int redPin = 3;
int greenPin = 4;
int bluePin = 5;

int c = 0;

void setup()
{
  Serial.begin(9600);  
  pinMode(redPin,OUTPUT);
  pinMode(greenPin,OUTPUT);
  pinMode(bluePin,OUTPUT);
}

void loop()
{
  if(Serial.available());
  c = Serial.read();
  if (c == 97)  //a in ASCII is 97
  {
    digitalWrite(redPin,HIGH);   
    delay(500);
    digitalWrite(redPin,LOW); 
  }
  if (c == 98)  //b in ASCII is 98
  {
    digitalWrite(greenPin,HIGH);   
    delay(500);
    digitalWrite(greenPin,LOW);    
  }
  if (c == 99)  
  {
    digitalWrite(bluePin,HIGH);   
    delay(500);
    digitalWrite(bluePin,LOW);
  }
}
```

### Processing Side:

```java
import processing.serial.*;
Serial port;

void setup(){
  port=new Serial(this,"COM5",9600); //Arduino's com
  size(600,200);
}

void draw(){
  fill(255,0,0);
  rect(50,50,100,100);

  fill(0,255,0);
  rect(250,50,100,100);

  fill(0,0,255);
  rect(450,50,100,100);  
}

void mouseClicked(){
  if((mouseX>=50)&(mouseX<=150)&(mouseY>=50)&(mouseY<=150))
  {
    println("red");
    port.write("a");
  }
  else if((mouseX>=250)&(mouseX<=350)&(mouseY>=50)&(mouseY<=150))
  {
    println("green");
    port.write("b");
  }
  else if((mouseX>=450)&(mouseX<=550)&(mouseY>=50)&(mouseY<=150))
  {
    println("blue");
    port.write("c");
  }
}


```
### Notes

1. Ensure that Arduino and the computer use the same baud rate (9600 in this example).
   
2. Close the serial monitor in both Arduino and Processing as only one program can access the serial port at a time.
   
3. Handle potential exceptions and errors, such as dealing with different data types or incorrect port names.

## Display

<video src="img/IAP/dis.mp4" width="1080px" height="500px" controls="controls"></video>

## Wiring Method

We use 1K ohm resistance.

<img src="img/IAP/wire2.png" width=1080>

## Code

### Processing Side:

```java
import processing.serial.*;
Serial port;

void setup(){
  port=new Serial(this,"COM4",9600); //Arduino板的端口号
  size(600,200);
}

void draw(){
  fill(255,0,0);
  rect(50,50,100,100);

  fill(0,255,0);
  rect(250,50,100,100);

  fill(0,0,255);
  rect(450,50,100,100);  
}

void mouseClicked(){
  if((mouseX>=50)&(mouseX<=150)&(mouseY>=50)&(mouseY<=150))
  {
    println("red");
    port.write("a");
  }
  else if((mouseX>=250)&(mouseX<=350)&(mouseY>=50)&(mouseY<=150))
  {
    println("green");
    port.write("b");
  }
  else if((mouseX>=450)&(mouseX<=550)&(mouseY>=50)&(mouseY<=150))
  {
    println("blue");
    port.write("c");
  }
}

```

### Arduino Side:
```c
int redPin = 3;
int greenPin = 4;
int bluePin = 5;

int c = 0;

void setup()
{
  Serial.begin(9600); 
  pinMode(redPin,OUTPUT);
  pinMode(greenPin,OUTPUT);
  pinMode(bluePin,OUTPUT);
}

void loop()
{
  if(Serial.available());
  c = Serial.read();
  if (c == 97)  
  {
    digitalWrite(redPin,HIGH);   
    delay(500);
    digitalWrite(redPin,LOW); 
  }
  if (c == 98) 
  {
    digitalWrite(greenPin,HIGH);   
    delay(500);
    digitalWrite(greenPin,LOW);    
  }
  if (c == 99)  
  {
    digitalWrite(bluePin,HIGH);   
    delay(500);
    digitalWrite(bluePin,LOW);
  }
}

```