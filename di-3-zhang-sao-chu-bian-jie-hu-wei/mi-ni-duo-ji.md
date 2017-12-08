# 迷你舵机

![](/assets/迷你舵机.png)

舵机是一种位置（角度）伺服的驱动器，适用于那些需要角度不断变化并可以保持的控制系统。舵机是船舶上的一种大甲板机械。

# 连线图

![](/assets/迷你舵机连接.png)

## Arduino 代码

```cpp
#include <Servo.h> 

Servo myservo;  // 创建一个舵机控制对象
int PinServer = 8;
int pos = 0;    // 该变量用与存储舵机角度位置

void setup() 
{ 
  myservo.attach(PinServer);  // 该舵机由arduino第九脚控制
} 

void loop() 
{ 
  for(pos = 0; pos < 180; pos += 1)  // 从0度到180度运动 
  {
    myservo.write(pos); // 指定舵机转向的角度
    delay(15); // 等待15ms让舵机到达指定位置
  } 

  for(pos = 180; pos>=1; pos-=1)   //从180度到0度运动  
  {                                
    myservo.write(pos); // 指定舵机转向的角度 
    delay(15); // 等待15ms让舵机到达指定位置 
  } 
}
```



