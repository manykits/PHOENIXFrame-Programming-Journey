# 激光头传感器模块

![](/assets/jiguangtou.png)

**工作电压： 5V  **

## 连接图

+接5V

-接GND

S接信号

## Arduino 代码

```cpp
int PinLaser= 13;

void setup()
{
  pinMode(PinLaser, OUTPUT); // 定义13脚为数字输出接口 
}

void loop()
{
  digitalWrite(PinLaser, HIGH); // 打开激光头
  delay(1000); // 延时一秒
  digitalWrite(PinLaser, LOW); // 关闭激光头
  delay(1000); // 延时一秒
}
```



