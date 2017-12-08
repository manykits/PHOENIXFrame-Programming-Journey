## 麦克风传感器模块

![](/assets/import.png)

## 准备材料

电池

麦克风传感器模块

杜邦线

## 连接图

![](/assets/v2.png)

## 使用方法

模块有2个输出

1. AO，模拟量输出，实时输出麦克风的电压信号
2. DO，当声音强度到达某个阀值时，输出高低电平信号，\(阀值-灵敏度可以通过电位器调节\)

## Arduino 代码

1.模拟输出，使用AO：

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
int PinDO = A5;
int PinLed = 13;
int Val = 0;
void setup()
{
  pinMode(PinLed,OUTPUT); //定义LED 为输出接口
  pinMode(PinDO,INPUT); //定义传感器D0为输出
  Serial.begin(9600);
}
void loop()
{
  Val = digitalRead(PinDO);
  if (Val == HIGH) //当声音检测模块检测有信号时，LED亮
  {
    digitalWrite(PinLed, LOW) ;
    Serial.println("Recved HIGH");
  }
  else
  {
    digitalWrite(PinLed, HIGH) ;
    Serial.println("Recved LOW");
    delay(1000);
  }
}
```



