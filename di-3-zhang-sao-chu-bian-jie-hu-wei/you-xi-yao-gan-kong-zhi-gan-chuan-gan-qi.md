# 游戏摇杆控制杆传感器

# 介绍

PS2双轴按键游戏摇杆模块采用SONY公司PS2游戏手柄上原装优质金属按键摇杆电位器，模块特设二路模拟输出和一路数字输出接口，输出值分别对应（X，Y）双轴偏移量，其类型 为模拟量；按键表示用户是否在Z轴上按下，其类型为数字开关量。模块集成电源指示灯，可显示工作状态；坐标标识符清晰简明、准确定位；用其可以轻松控制物 体（如二自由度舵机云台）在二维空间运动，因此可以通过控制器编程，传感器扩展板插接，完成具有创意性遥控互动作品。

PS2游戏摇杆可在各种单片机控制器上应用，尤其在Arduino控制器上更为简单，通过3P传感器连接线插接到Arduino专用传感器扩展板上，可以非常容易的进行操作。

## 特点

1. 工作电压 ：+5v
2. 尺寸大小： 50mm x 28mm
3. 重量大小：133g
4. 信号类型：模拟信号
5. 接口类型：KF2510-5P

## 连接图

1. Y：Y轴方向信号引脚（模拟输出）

2. X：X轴方向信号引脚（模拟输出）
3. B：B轴方向信号引脚（数字输出）
4. GND：电源地
5. VCC：电源正极

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



