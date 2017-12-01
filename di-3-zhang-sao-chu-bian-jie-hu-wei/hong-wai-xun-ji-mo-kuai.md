## 红外循迹模块

![](/assets/循迹模块1.png)

## 特点

1. 工作电压：3-6V
2. 输出信号：数字电平0或1,
3. 灵敏度调节方式：精密电位器
4. 感应距离范围：2mm~20mm

## 功能介绍

## 准备材料

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



