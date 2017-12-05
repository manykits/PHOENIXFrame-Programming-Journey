# 双色LED模块

![](/assets/双色LED模块1.png)

双色LED是一种可以显示二色颜色的LED灯,  可以有三种状态:  灭,  颜色1亮, 颜色2亮 .  根据颜色组合的不同,  分为红蓝双色,  黄蓝双色, 红绿双色，红黄双色等等.

# 特点

发光颜色：红色+黄色

## 连接图

![](/assets/双色LED连接图.png)

用杜邦线把模块三个脚分别接到开发板上，其中把"-"线接 GND,   中间的脚接D7， "S"脚接D8

当中间管脚为高电平，则LED亮灯为一种颜色

当S管脚为高电平，则LED亮灯为另一种颜色

## Arduino 代码

```cpp
int Pin1 = 7; // 双色LED管脚中间  
int Pin2 = 8; // 双色LED管脚S

void setup() 
{   
  pinMode(Pin1, OUTPUT); 
  pinMode(Pin2, OUTPUT);
}  

void loop()
{   
  //熄灭  
  digitalWrite(Pin1, LOW);
  digitalWrite(Pin2, LOW);
  delay(1000);

  //颜色1亮  
  digitalWrite(Pin1, HIGH);
  digitalWrite(Pin2, LOW);
  delay(1000);

  // 颜色2亮  
  digitalWrite(Pin1, LOW);
  digitalWrite(Pin2, HIGH);
  delay(1000);

  // 颜色1亮 + 颜色2亮 （形成混合色）  
  digitalWrite(Pin1, HIGH);
  digitalWrite(Pin2, HIGH);
  delay(1000);
}
```



