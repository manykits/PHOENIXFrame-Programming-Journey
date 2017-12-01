## 面包板

包板是由于板子上有很多小插孔，专为电子电路的无焊接实验设计制造的。由于各种电子元器件可根据需要随意插入或拔出，免去了焊接，节省了电路的组装时间，而且元件可以重复使用，所以非常适合电子电路的组装、调试和训练。

## 连接图

## 使用方法

模块有2个输出

1. AO，模拟量输出，实时输出麦克风的电压信号
2. DO，当声音强度到达某个阀值时，输出高低电平信号，\(阀值-灵敏度可以通过电位器调节\)

## Arduino 代码

1.数字输出

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
int sensorPin = A5; 
int ledPin = 13;

void setup()
{
 pinMode(ledPin, OUTPUT); 
 Serial.begin(9600);
}
void loop()
{
 sensorValue = analogRead(sensorPin);    
 digitalWrite(ledPin, HIGH);  
 delay(sensorValue);
 digitalWrite(ledPin, LOW);  
 delay(sensorValue);
 Serial.println(sensorValue, DEC);  
}
```



