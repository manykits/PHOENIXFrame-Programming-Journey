## 温湿度传感器



DHT11 数字温湿度传感器是一款含有已校准数字信号输出的温湿度复合传感器，它应用专用的数字模块采集技术和温湿度传感技术，确保产品具有极高的可靠性和卓越的长期稳定性。单线制串行接口，使系统集成变得简易快捷。超小的体积、极低的功耗，信号传输距离可达 20 米以上。

## 特点

供电电压： 3.3~5.5V DC

输出： 单总线数字信号

测量范围： 湿度 20-90%RH， 温度 0~50℃

测量精度： 湿度+-5%RH， 温度+-2℃

分辨率： 湿度 1%RH， 温度 1℃

长期稳定性： &lt;±1%RH/年

# 注意事项

1. 避免在结露情况下使用
2. 长期保存温度 10-40℃，湿度 60%以下
3. 使用时电源和地接法要正确，**切勿将VCC与GND接反， **以免损坏传感器

## 准备材料

电池

温湿度传感器

杜邦线

## 连接图

# Arduino 代码

```cpp
#include "dht11.h"

dht11 DHT11;

double Fahrenheit(double celsius) 
{
    return 1.8 * celsius + 32;
}   

double Kelvin(double celsius)
{
    return celsius + 273.15;
}    

double dewPoint(double celsius, double humidity)
{
    double A0= 373.15/(273.15 + celsius);
    double SUM = -7.90298 * (A0-1);
    SUM += 5.02808 * log10(A0);
    SUM += -1.3816e-7 * (pow(10, (11.344*(1-1/A0)))-1) ;
    SUM += 8.1328e-3 * (pow(10,(-3.49149*(A0-1)))-1) ;
    SUM += log10(1013.246);
    double VP = pow(10, SUM-3) * humidity;
    double T = log(VP/0.61078);   // temp var
    return (241.88 * T) / (17.558-T);
}

double dewPointFast(double celsius, double humidity)
{
    double a = 17.271;
    double b = 237.7;
    double temp = (a * celsius) / (b + celsius) + log(humidity/100);
    double Td = (b * temp) / (a - temp);
    return Td;
}


#define DHT11PIN 2

void setup()
{
  Serial.begin(9600);
  Serial.println("DHT11 TEST PROGRAM ");
  Serial.print("LIBRARY VERSION: ");
  Serial.println(DHT11LIB_VERSION);
  Serial.println();
}

void loop()
{
  Serial.println("\n");

  int chk = DHT11.read(DHT11PIN);

  Serial.print("Read sensor: ");
  switch (chk)
  {
    case DHTLIB_OK: 
        Serial.println("OK"); 
        break;
    case DHTLIB_ERROR_CHECKSUM: 
        Serial.println("Checksum error"); 
        break;
    case DHTLIB_ERROR_TIMEOUT: 
        Serial.println("Time out error"); 
        break;
    default: 
        Serial.println("Unknown error"); 
        break;
  }

  Serial.print("Humidity (%): ");
  Serial.println((float)DHT11.humidity, 2);

  Serial.print("Temperature (oC): ");
  Serial.println((float)DHT11.temperature, 2);

  Serial.print("Temperature (oF): ");
  Serial.println(Fahrenheit(DHT11.temperature), 2);

  Serial.print("Temperature (K): ");
  Serial.println(Kelvin(DHT11.temperature), 2);

  Serial.print("Dew Point (oC): ");
  Serial.println(dewPoint(DHT11.temperature, DHT11.humidity));

  Serial.print("Dew PointFast (oC): ");
  Serial.println(dewPointFast(DHT11.temperature, DHT11.humidity));
  delay(2000);
}
```



