# 三色RGB LED

RGB三个针，分别接三个数字口，进行控制。通过控制各个引脚，调整RGB三个灯的输出达到控制整个颜色的效果。

# 连线图

## Arduino 代码

```cpp
int PinRed = 9;
int PinGreen = 10;
int PinBlue = 11;

void setup()
{
  pinMode(PinRed, OUTPUT);
  pinMode(PinGreen, OUTPUT);
  pinMode(PinBlue, OUTPUT);
}

// constrain(amt，low，high)函数的工作过程是，如果值amt小于low，则返回low
// 如果amt大于high，则返回high；否则，返回amt
// 该函数一般可以用于将值归一化到某个区间内
void colorRGB(int red, int green, int blue)
{
  analogWrite(PinRed, constrain(red,0,255));
  analogWrite(PinGreen, constrain(green,0,255));
  analogWrite(PinBlue, constrain(blue,0,255));
}

void loop()
{
  // R:0-255 G:0-255 B:0-255
  colorRGB(random(0,255),random(0,255),random(0,255));  
  delay(500);
}
```



