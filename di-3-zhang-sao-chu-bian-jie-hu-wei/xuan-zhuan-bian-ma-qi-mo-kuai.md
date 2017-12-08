# 旋转编码器模块

![](/assets/xuanzhuan.png)

旋转编码器可通过旋转可以计数正方向和反方向转动过程中输出脉冲的次数，旋转计数不像电位计，这 种转动计数是没有限制的。配合旋转编码器上的按键，可以复位到初始状态，即从0开始计数。

旋转编码器的操作是旋转和按压转轴，在按下转轴的时候SW引脚的电平会变化，旋转的时候每转动一步CLK和DT的电平是有规律的变化。

## 连接图

Switch（开关）、CLK是Clock（时钟）、DT是Data（数据）

## Arduino应该是

```cpp
int CLK = 2; //CLK->D2
int DT = 3; //DT->D3
int SW = 4; //SW->D4
const int interrupt0 = 0;// Interrupt 0 在 pin 2 上
int count = 0;//计数值
int lastCLK = 0;//CLK历史值

void ClockChanged()
{
  int clkValue = digitalRead(CLK);//读取CLK引脚的电平
  int dtValue = digitalRead(DT);//读取DT引脚的电平
  if (lastCLK != clkValue)
  {
    lastCLK = clkValue;
    count += (clkValue != dtValue ? 1 : -1);//CLK和DT不一致时+1，否则-1
    Serial.print("count:");
    Serial.println(count);
  }
}
 
 void setup()
{
  pinMode(SW, INPUT);
  digitalWrite(SW, HIGH);
  pinMode(CLK, INPUT);
  pinMode(DT, INPUT);
  attachInterrupt(interrupt0, ClockChanged, CHANGE); // 设置中断0的处理函数，电平变化触发
  Serial.begin(9600);
}
  
void loop()
{
  if (!digitalRead(SW) && count != 0) //读取到按钮按下并且计数值不为0时把计数器清零
  {
     count = 0;
     Serial.print("count:");
     Serial.println(count);
   }
}
```



