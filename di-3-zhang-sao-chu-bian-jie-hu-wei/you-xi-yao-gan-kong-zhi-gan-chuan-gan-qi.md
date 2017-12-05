# 游戏摇杆控制杆传感器



# 介绍

PS2双轴按键游戏摇杆模块采用SONY公司PS2游戏手柄上原装优质金属按键摇杆电位器，模块特设二路模拟输出和一路数字输出接口，输出值分别对应（X，Y）双轴偏移量，其类型 为模拟量；按键表示用户是否在Z轴上按下，其类型为数字开关量。模块集成电源指示灯，可显示工作状态；坐标标识符清晰简明、准确定位；用其可以轻松控制物 体（如二自由度舵机云台）在二维空间运动，因此可以通过控制器编程，传感器扩展板插接，完成具有创意性遥控互动作品。

PS2游戏摇杆可在各种单片机控制器上应用，尤其在Arduino控制器上更为简单，通过3P传感器连接线插接到Arduino专用传感器扩展板上，可以非常容易的进行操作。

## 连接图

VCC：电源正极

GND：电源地

VRX，VRY，SW引脚接到控制器的A0,A1,A2口

## Arduino 代码

```cpp
int X;
int Y;
int B;
void setup()
{   
  Serial.begin(9600);
} 
void loop()
{           
  X = analogRead(A0);      //读取A0口模拟值
  Y = analogRead(A1);      //读取A1口模拟值
  B = analogRead(A2);      //读取A2口模拟值
  Serial.println(X);
  Serial.println(Y);
  Serial.println(B);
  delay(1000);
}
```



