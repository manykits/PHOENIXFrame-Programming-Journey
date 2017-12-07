# 轻触开关模块

![](/assets/qingchukaiguan.png)

按键是一种常用的控制电器元件，常用来接通或断开电路，从而达到控制电机或者其他设备运行的开关

## 连接图

![](/assets/轻触开关连接.png)

## Arduino 代码

```
int PinLed=13; // 定义LED 接口
int PinButton=8; // 定义按键开关传感器接口 ;
int Val = 0; // 定义数字变量val

void setup()
{
  pinMode(PinLed, OUTPUT); // 定义LED 为输出接口
  pinMode(PinButton, INPUT);
}

void loop()
{
  Val=digitalRead(PinButton); //将数字接口PinButton的值读取赋给val
  if (Val==HIGH)//当按键开关传感器检测有信号时，LED 闪烁 
  {
    digitalWrite(PinLed, HIGH);
  }
  else
  {
    digitalWrite(PinLed, LOW);
  }
}
```



