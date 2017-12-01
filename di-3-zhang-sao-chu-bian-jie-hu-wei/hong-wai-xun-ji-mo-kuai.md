## 红外循迹模块

![](/assets/循迹模块1.png)

## 特点

1. 工作电压：3-6V
2. 输出信号：数字电平0或1,
3. 灵敏度调节方式：精密电位器
4. 感应距离范围：2mm~20mm

## 功能介绍

1. 传感器的红外发射二极管不断发射红外线，当发射出的红外线没有被反射回来或被反射回来但强度不够大时，红外接收管一直处于关断状态，此时模块的输出端为高电平，指示二极管一直处于熄灭状态；被检测物体出现在检测范围内时，红外线被反射回来且强度足够大，红外接收管饱和，此时模块的输出端为低电平，指示二极管被点亮。
2. 当模块检测到前方障碍物信号时，电路板上绿色指示灯点亮电平，同时OUT端口持续输出低电平信号,该模块检测距离2～30cm，检测角度35°，检测距离可以通过电位器进行调节，顺时针调电位器，检测距离增加；逆时针调电位器，检测距离减少。
3. 传感器主动红外线反射探测,因此目标的反射率和形状是探测距离的关键。其中黑色探测距离小,白色大;小面积物体距离小,大面积距离大。

## 准备材料

电池

红外循迹模块

杜邦线

## 连接图

## Arduino 代码

1.模拟输出，使用AO

```cpp
int PinAO = A5;
int PinLed = 13;

void setup()
{
  pinMode(PinLed, OUTPUT);
  Serial.begin(9600);
}
void loop()
{
  int sensorValue = analogRead(PinAO);    
  digitalWrite(PinLed, HIGH);
  delay(sensorValue);
  digitalWrite(PinLed, LOW);
  delay(sensorValue);

  Serial.println(sensorValue, DEC);
}
```

2.数字输出，使用DO

```cpp
int PinAO = A5; // 定义寻线传感器接口
int PinLed = 13; // 定义LED 接口
int Val = 0; // 定义数字变量val

void setup()
{
  pinMode(PinLed, OUTPUT); // 定义LED 为输出接口
  pinMode(PinAO, INPUT); // 定义寻线传感器为输出接口
  Serial.begin(9600);
}
void loop()
{
  Val = digitalRead(PinAO); // 将数字接口3的值读取赋给val
  if (Val == HIGH) // 当寻线传感器检测有信号时，LED 闪烁
  {
    digitalWrite(PinLed, LOW);
    Serial.println("HIGH");
  }
  else
  {
    digitalWrite(PinLed, HIGH);
    Serial.println("LOW");
  }
}
```



