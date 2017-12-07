# 七彩自动闪烁LED模块

![](/assets/七彩自动闪烁LED模块1.png)

7彩自动闪烁LED模块采用了5mm圆头高亮度发光二极管，该二极管具有以下特点：

1. 产品类型：发光二极管
2. 产品型号:YB-3120B4PnYG-PM
3. 产品形状:直插型5mm圆头发光二极管
4. 发光颜色:粉 黄 绿\(高亮度\)
5. 镜头类型:白色雾状
6. 标准正向电压:3.0-4.5V

## 准备材料

电池

七彩自动闪烁

杜邦线

## 连接图

![](/assets/七彩自动闪烁连接.png)

## Arduino 代码

```cpp
int PinLED = 8;
void setup()
{
  pinMode(PinLED, OUTPUT);
}

void loop()
{
  digitalWrite(PinLED, HIGH);
  delay(500);
  digitalWrite(PinLED, LOW);
  delay(500);
}
```



