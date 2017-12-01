## 红外循迹模块

![](/assets/循迹模块1.png)

## 特点

1. 工作电压：3-6V
2. 输出信号：数字电平0或1,
3. 灵敏度调节方式：精密电位器
4. 感应距离范围：2mm~20mm

## 功能介绍

传感器的红外发射二极管不断发射红外线，当发射出的红外线没有被反射回来或被反射回来但强度不够大时，红外接收管一直处于关断状态，此时模块的输出端为高电平，指示二极管一直处于熄灭状态；被检测物体出现在检测范围内时，红外线被反射回来且强度足够大，红外接收管饱和，此时模块的输出端为低电平，指示二极管被点亮。

## 准备材料



## 连接图

## Arduino 代码

```cpp
int Led=13;//定义LED 接口
int buttonpin=3; //定义寻线传感器接口 
int val;//定义数字变量val 

void setup() 
{
    pinMode(Led,OUTPUT);//定义LED 为输出接口 
    pinMode(buttonpin,INPUT);//定义寻线传感器为输出接口
}
void loop()
{
    val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
    if(val==HIGH) //当寻线传感器检测有信号时，LED 闪烁 
    {
        digitalWrite(Led,HIGH);
    }
    else 
    {
        digitalWrite(Led,LOW);
    }
}
```



