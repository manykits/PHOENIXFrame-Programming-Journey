# 4位数码管显示模块

![](/assets/4weishuma.png)

## 特点

1. 工作电压：3.3v
2. 8个调节亮度的级别

# 连线图

控制接口：共4个引脚（GND·VCC·DIO·CLK），GND为地，VCC为供电电源，DIO为数据输入输出脚，CLK为时钟信号脚。

## Arduino 代码

```cpp
#include "TM1637.h"
#define PinCLK 2
#define PinDIO 3
TM1637 tm1637(PinCLK, PinDIO);

int8_t NumTab[] = {0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};//0~9,A,b,C,d,E,F
void setup()
{
    tm1637.init();
    tm1637.set(BRIGHTEST); // BRIGHT_TYPICAL = 2,BRIGHT_DARKEST = 0,BRIGHTEST = 7;
    tm1637.point(true);
}
void loop()
{
    tm1637.display(0, NumTab[0]);
    tm1637.display(1, NumTab[1]);
    tm1637.display(2, NumTab[2]);
    tm1637.display(3, NumTab[3]);
    delay(1000);
    tm1637.display(0, NumTab[4]);
    tm1637.display(1, NumTab[5]);
    tm1637.display(2, NumTab[6]);
    tm1637.display(3, NumTab[7]);
    delay(1000);
}
```



