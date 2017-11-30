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



