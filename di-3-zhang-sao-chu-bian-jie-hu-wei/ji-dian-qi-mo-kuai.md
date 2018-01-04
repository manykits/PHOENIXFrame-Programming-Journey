继电器模块

![](/assets/继电器模块4.png)

继电器是一种电控制器件，是当输入量（激励量）的变化达到规定要求时，在电气输出电路中使被控量发生预定的阶跃变化的一种电器。它具有控制系统（又称输入回路）和被控制系统（又称输出回路）之间的互动关系。通常应用于自动化的控制电路中，它实际上是用小电流去控制大电流运作的一种“自动开关”。故在电路中起着自动调节、安全保护、转换电路等作用。

## 特点

输出驱动能力：250VAC-10A、125VAC-10A、30VDC-10A、28VDC-10A

工作电压5V，吸合电流约70mA每路，带继电器状态指示灯

# 注意事项

## 准备材料

电池

继电器模块

杜邦线

## 连接图

![](/assets/jidianqilianjie.png)

![](/assets/继电器链接图.png)

输入端

+：控制信号正级

-：控制信号负级

S：控制信号

输出端

NC：继电器常闭接，继电器吸合前与COM短接，吸合后悬空

COM：继电器通电公用接口

NO：继电器常开接口，继电器吸合前悬空，吸合后与COM短接

# Arduino 代码

```cpp
int PinJDQ = 8; 

void setup()
{
  pinMode(PinJDQ, OUTPUT); 
} 

void loop(){
  digitalWrite(PinJDQ, HIGH);
  delay(2000);
  digitalWrite(PinJDQ, LOW); //LOW to poweroff the LED light on jidianqi
  delay(5000);
}
```



