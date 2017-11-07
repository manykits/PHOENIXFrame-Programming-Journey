# 介绍

发光颜色：绿色+红色

使用电压\(V\)：2.0-2.5

使用电流\(MA\)：10

## Arduino 代码

```cpp
//Arduino test code: int redpin = 11;  
// select the pin for the red LED
int bluepin =10; // select the pin for the blueLED int val;
void setup()
{
 pinMode(redpin, OUTPUT); 
 pinMode(bluepin, OUTPUT);
 Serial.begin(9600); 
}
void loop()
{ 
 for(val=255; val>0; val--)
 {
  analogWrite(11, val); 
  analogWrite(10, 255-val);
  delay(15);  
 }
 for(val=0; val<255; val++)
 {
  analogWrite(11, val); 
  analogWrite(10, 255-val); 
  delay(15);  
 } 
 Serial.println(val, DEC);
}
```



