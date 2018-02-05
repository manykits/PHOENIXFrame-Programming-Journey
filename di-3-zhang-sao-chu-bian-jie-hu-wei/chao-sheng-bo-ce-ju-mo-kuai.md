# 超声波测距模块

![](/assets/超声波模块.png)

超声波发射器向某一方向发射超声波，在发射的同时开始计时，超声波在空气中传播，途中碰到障碍物就立即返回来，超声波接收器收到反射波就立即停止计时。声波在空气中的传播速度为

340m/s，根据计时器记录的时间t，就可以计算出发射点距障碍物的距离s，即：s=340m/s×t / 2。

## 特点

1. 使用电压：DC---5V 
2. 静态电流：小于2mA  
3. 电平输出：高5V 
4. 电平输出：底0V  
5. 感应角度：不大于15度
6. 探测距离：2cm-450cm 
7. 高精度可达0.2cm  

## 连接图

![](/assets/超声波连接.png)

## Arduino 代码

```cpp
#include "PXFNewPing.h"

int PinTrig = 7;
int PinEcho = 8;

#define MAX_DISTANCE 200
NewPing newPin(PinTrig, PinEcho, MAX_DISTANCE); // NewPing setup of pins and maximum distance.

void setup()
{
  Serial.begin(9600);
}

void loop() 
{
  delay(30.0);
  int dist = newPin.ping_cm();
  Serial.print(dist);
  Serial.println(" cm");
}
```



