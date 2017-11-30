# 七彩自动闪烁LED模块

# 介绍

7彩自动闪烁LED模块采用了5mm圆头高亮度发光二极管，该二极管具有以下特点：

1. 产品类型：发光二极管
2. 产品型号:YB-3120B4PnYG-PM
3. 产品形状:直插型5mm圆头发光二极管
4. 发光颜色:粉 黄 绿\(高亮度\)
5. 镜头类型:白色雾状
6. 标准正向电压:3.0-4.5V

## Arduino 代码

```cpp
void setup()
{
  pinMode(13, OUTPUT);    
}

void loop() 
{  
  digitalWrite(13, HIGH);// set the LED on  
  delay(2000); // wait for a second  
  digitalWrite(13, LOW);  // set the LED off  
  delay(2000); // wait for a second
}
```



