## 麦克风传感器模块

![](/assets/import.png)

## 准备材料

电池

面包版电源扩展版

面包版

麦克风传感器模块

杜邦线

## 连接图

## 使用方法

模块有2个输出

1. AO，模拟量输出，实时输出麦克风的电压信号
2. DO，当声音强度到达某个阀值时，输出高低电平信号，\(阀值-灵敏度可以通过电位器调节\)

## Arduino 代码

1.数字输出，使用DO

```cpp
int led = 13;
int buttonpin = 3;
int val;
void setup()
{
  pinMode(Led,OUTPUT);//定义LED 为输出接口
  pinMode(buttonpin,INPUT);//定义传感器D0为输出
}
void loop()
{
  val=digitalRead(buttonpin); 
  if(val==HIGH)//当声音检测模块检测有信号时，LED 闪烁
  {
    digitalWrite(Led,HIGH) ;
  }
  else
  {
    digitalWrite(Led,LOW) ;
  }
}
```

2.模拟输出：

```cpp
int PinSensor = A5;
int PinLed = 13;

void setup()
{
  pinMode(PinLed, OUTPUT);
  Serial.begin(9600);
}
void loop()
{
  int sensorValue = analogRead(PinSensor);    
  digitalWrite(PinLed, HIGH);
  delay(sensorValue);
  digitalWrite(PinLed, LOW);
  delay(sensorValue);
  
  Serial.println(sensorValue, DEC);
}
```



