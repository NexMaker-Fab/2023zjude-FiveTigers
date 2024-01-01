# Running water lamps

## Achievement display

<img src="img/arduino/water.gif" width=1920>


## Circuit connection

This project uses a 1k ohm resistor.

<img src="img/arduino/water1.png" width=1920>

## Code display

```c

  void setup() 
  { 
    for(int i = 9; i <= 13; i++)
    {
    pinMode(i, OUTPUT);
    }
  }

  void loop() 
  {
        digitalWrite(13,LOW);
        digitalWrite(9,HIGH);
        delay(200);

        digitalWrite(9,LOW);
        digitalWrite(10,HIGH);
        delay(200);

        digitalWrite(10,LOW);
        digitalWrite(11,HIGH);
        delay(200);

        digitalWrite(11,LOW);
        digitalWrite(12,HIGH);
        delay(200);

        digitalWrite(12,LOW);
        digitalWrite(13,HIGH);
        delay(200);
  }

```