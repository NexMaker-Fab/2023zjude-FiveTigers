# Smoke detection lights

## Required Materials
1. Arduino Uno
2. LED
3. DuPont Wire
4. MQ-2 Smoke sensor
   
## Display

The MQ-2 can detect the flammable gas of the lighter, and the LED light flashes when the flammable gas is present.

<video src="img/arduino/smoke/smoke2.mp4" width="1080px" height="500px" controls="controls"></video>



## Introduction
MQ-2 is commonly used for gas leakage monitoring in homes and factories, suitable for detecting liquefied gas, benzene, propane, alcohol, hydrogen, smoke, and other gases. Therefore, MQ-2 can accurately be described as a multi-gas detector. MQ-2 has an extremely wide detection range. Its advantages include high sensitivity, fast response, good stability, long life, and a simple drive circuit.

<img src="img/arduino/smoke/sam.png" width=1080>

<!--Schematic diagram of wiring
<img src="img/arduino/smoke/test.png" width=1080>-->

## Circuit connection

Here, LED RGB is used instead of the smoke sensor

<img src="img/arduino/smoke/link.png" width=1080>

<img src="img/arduino/smoke/img.jpg" width=1080>

This project uses a 1k ohm resistor.

## Code display

```c
 #define MQ2pin (0)
 float sensorValue;
// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600); // sets the serial port to 9600
 Serial.println("Gas sensor warming up!");
 pinMode(5,OUTPUT);
 digitalWrite(5,LOW);
 delay(20000); // allow the MQ-6 to warm up
}

// the loop routine runs over and over again forever:
void loop() {
sensorValue = analogRead(MQ2pin); // read analog input pin 0
   
   Serial.print("Sensor Value: ");
   Serial.print(sensorValue);
   delay(20);
   if(sensorValue > 170)
   {
    
    digitalWrite(5,HIGH);
    Serial.print(" | Smoke detected!");
    delay(10);
   }
    digitalWrite(5,LOW);
   
   Serial.println("");
   delay(2000); // wait 2s for next reading
}
```