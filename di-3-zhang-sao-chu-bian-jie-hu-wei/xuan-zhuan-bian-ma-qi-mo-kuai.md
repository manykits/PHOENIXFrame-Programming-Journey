# 旋转编码器模块

![](/assets/xuanzhuan.png)

旋转编码器可通过旋转可以计数正方向和反方向转动过程中输出脉冲的次数，旋转计数不像电位计，这 种转动计数是没有限制的。配合旋转编码器上的按键，可以复位到初始状态，即从0开始计数。

旋转编码器的操作是旋转和按压转轴，在按下转轴的时候SW引脚的电平会变化，旋转的时候每转动一步CLK和DT的电平是有规律的变化。

点击：SW+GND时按下和松开按钮没有任何变化，VCC+SW松开时表针指向0，按下时高电平。据此可以推测SW平时为高阻态，按下时接地。用Arduino检测的方法是设置连接SW的引脚为INPUT并上拉输出高电平，检测到引脚为低电平则表示按钮按下，以下代码可以正确检测出按钮的变化。

旋转：CLK+GND，每旋转一次（和方向无关），电平转换一次，DT（红）+GND（黑），变化情况和上一种情况一致，并且CLK和DT的电平保持一致。VCC（红）+CLK（黑），VCC（红）+DT（黑）也是同样的情况。CLK（红）+DT（黑）或者CLK（黑）+DT（红）时，每次旋转（和方向无关）指针都会轻微摆动然后归零，并且相邻两步指针的摆动方向相反。结论：每次旋转CLK和DAT引脚的电平都会变化，电平变化有时间差，但无法区分往哪个方向旋转

## 连接图

Switch（开关）、CLK是Clock（时钟）、DT是Data（数据）

## Arduino应该是

```cpp
int redPin = 2; 
int yellowPin = 3;
int greenPin = 4; 
int aPin = 6; 
int bPin = 7;
int buttonPin = 5;
int state = 0; 
int longPeriod = 5000; // Time at green or red int shortPeriod = 700; // Time period when changing int targetCount = shortPeriod; int count = 0;

void setup() 
{
 pinMode(aPin, INPUT); 
 pinMode(bPin, INPUT); 
 pinMode(buttonPin, INPUT); 
 pinMode(redPin, OUTPUT); 
 pinMode(yellowPin, OUTPUT); 
 pinMode(greenPin, OUTPUT); 
} 

void loop()
{
  count++;

  if (digitalRead(buttonPin)) 
  {
   setLights(HIGH, HIGH, HIGH);
  } 
  else 
  { 
   int change = getEncoderTurn(); 
   int newPeriod = longPeriod + (change * 1000);  

   if (newPeriod >= 1000 && newPeriod <= 10000)
   {
    longPeriod = newPeriod;
   }

   if (count > targetCount)
   {
    setState();
    count = 0;
   }    
  }
  delay(1); 
}

int getEncoderTurn() 
{ // return -1, 0, or +1
 static int oldA = LOW;
 static int oldB = LOW; 
 int result = 0; 
 int newA = digitalRead(aPin); 
 int newB = digitalRead(bPin);

 if (newA != oldA || newB != oldB)
 { // something has changed
  if (oldA == LOW && newA == HIGH)
  {
   result = -(oldB * 2 - 1); } } 
   oldA = newA; 
   oldB = newB; 
   return result; 
  } 

int setState() 
{ 
 if (state == 0) 
 { 
  setLights(HIGH, LOW, LOW); 
  targetCount = longPeriod; state = 1; 
 } 
 else if (state == 1) 
 {
  setLights(HIGH, HIGH, LOW);
  targetCount = shortPeriod;
  state = 2; 
 } 
 else if (state == 2)
 { 
  setLights(LOW, LOW, HIGH); 
  targetCount = longPeriod; 
  state = 3; 
 }
 else if (state == 3) 
 { 
  setLights(LOW, HIGH, LOW); 
  targetCount = shortPeriod; 
  state = 0;
 } 
}

void setLights(int red, int yellow, int green) 
{ 
 digitalWrite(redPin, red);
 digitalWrite(yellowPin, yellow); 
 digitalWrite(greenPin, green);
}
```



