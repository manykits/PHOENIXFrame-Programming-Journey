## 温湿度传感器

# 介绍

DHT11 数字温湿度传感器是一款含有已校准数字信号输出的温湿度复合传感器，它应用专用的数字模块采集技术和温湿度传感技术，确保产品具有极高的可靠性和卓越的长期稳定性。单线制串行接口，使系统集成变得简易快捷。超小的体积、极低的功耗，信号传输距离可达 20 米以上。

# 技术参数

供电电压： 3.3~5.5V DC

输 出： 单总线数字信号

测量范围： 湿度 20-90%RH， 温度 0~50℃

测量精度： 湿度+-5%RH， 温度+-2℃

分 辨 率： 湿度 1%RH， 温度 1℃

长期稳定性： &lt;±1%RH/年

# 注意事项

1. 避免在结露情况下使用
2. 长期保存温度 10-40℃，湿度 60%以下
3. 使用时电源和地接法要正确，**切勿将VCC与GND接反， **以免损坏传感器

# Arduino 代码

```cpp
int PinDH = 8;
byte dat[5];
byte ReadData()
{
  byte data;
  for(int i=0; i<8; i++)
  {
    if(digitalRead(PinDH) == LOW)
    {
      while(digitalRead(PinDH) == LOW); //等待 50us；
      delayMicroseconds(30); //判断高电平的持续时间，以判定数据是‘0’还是‘1’；
      if(digitalRead(PinDH) == HIGH)
      data |= (1<<(7-i)); //高位在前，低位在后；
      while(digitalRead(PinDH) == HIGH); //数据‘1’，等待下一位的接收；
    }
  }
  return data;
}

void StartTest()
{
  digitalWrite(PinDH,LOW); //拉低总线，发开始信号；
  delay(30); //延时要大于 18ms，以便 DHT11 能检测到开始信号；
  digitalWrite(PinDH,HIGH);
  delayMicroseconds(40); //等待 DHT11 响应；
  pinMode(PinDH,INPUT);
  while(digitalRead(PinDH) == HIGH);
  delayMicroseconds(80); //DHT11 发出响应，拉低总线 80us；
  if(digitalRead(PinDH) == LOW);
  delayMicroseconds(80); //DHT11 拉高总线 80us 后开始发送数据；
  for(int i=0;i<4;i++) //接收温湿度数据，校验位不考虑；
  dat[i] = ReadData();
  pinMode(PinDH,OUTPUT);
  digitalWrite(PinDH,HIGH); //发送完一次数据后释放总线，等待主机的下一次开始信号；
}

void setup()
{
  Serial.begin(9600);
  pinMode(PinDH, OUTPUT);
}

void loop()
{
  StartTest();
  Serial.print("Current humdity = ");
  Serial.print(dat[0], DEC); // 显示湿度的整数位；
  Serial.print('.');
  Serial.print(dat[1],DEC);  // 显示湿度的小数位；
  Serial.println('%');
  Serial.print("Current temperature = ");
  Serial.print(dat[2], DEC); // 显示温度的整数位；
  Serial.print('.');
  Serial.print(dat[3],DEC); // 显示温度的小数位；
  Serial.println('C');
  delay(700);
}
```



