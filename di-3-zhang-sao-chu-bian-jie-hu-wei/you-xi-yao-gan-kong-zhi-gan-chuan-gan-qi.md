# 游戏摇杆控制杆传感器

# 介绍

它就像一个在游戏控制台中操纵杆，你可以控制输入这个操纵杆模块的 x、y、z 的PS2摇杆 游戏摇杆模块 Joystick值以及在特定的值下实现某种功能，它可以被视为一个按钮和电位计的组合。数据类型的 x,y 维为模拟输入信号而 z 维是数字输入信号，因此,x 和 y 端口连接到模拟插脚传感器端,而 z 端口连接到数字端口。

## Arduino 代码

```cpp
int sensorPin = 5; 
int value = 0; 
void setup() 
{
    pinMode(7, OUTPUT); 
    Serial.begin(9600); 
}
void loop() 
{ 
    value = analogRead(0); 
    Serial.print("X:");
    Serial.print(value, DEC); 
    value = analogRead(1); 
    Serial.print(" | Y:"); 
    Serial.print(value, DEC);
    value = digitalRead(7); 
    Serial.print(" | Z: "); 
    Serial.println(value, DEC); 
    delay(100);
}
```



