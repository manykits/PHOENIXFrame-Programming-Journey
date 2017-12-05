# 双色LED模块

# 介绍

发光颜色：绿色+红色

使用电压\(V\)：2.0-2.5

使用电流\(MA\)：10

## 连接图

用杜邦线把模块三个脚分别接到开发板上，其中把"-"线接 GND,   中间的脚接D7， "S"脚接D8

## Arduino 代码

```cpp
int Pin1 = 7; //双色LED管脚中间  
int Pin2 = 8; //双色LED管脚S
  
void setup() 
{   
  pinMode(Pin1, OUTPUT); //设置管脚1为输出状态  
  pinMode(Pin2, OUTPUT); //设置管脚2为输出状态  
}  
  
void loop()
{   
  //熄灭  
  digitalWrite(Pin1, LOW);  //设置管脚1为LOW  
  digitalWrite(Pin2, LOW);  //设置管脚3为LOW  
  delay(1000); //等待1000毫秒  
  
  //颜色1亮  
  digitalWrite(Pin1, HIGH);  //设置管脚1为HIGH  
  digitalWrite(Pin2, LOW);  //设置管脚3为LOW  
  delay(1000); //等待1000毫秒  
    
  //颜色2亮  
  digitalWrite(Pin1, LOW);  //设置管脚1为LOW  
  digitalWrite(Pin2, HIGH);  //设置管脚3为HIGH  
  delay(1000); //等待1000毫秒  
  
  //颜色1亮 + 颜色2亮 （形成混合色）  
  digitalWrite(Pin1, HIGH);//设置管脚1为HIGH  
  digitalWrite(Pin2, HIGH);  //设置管脚3为HIGH  
  delay(1000); //等待1000毫秒  
}  
```



