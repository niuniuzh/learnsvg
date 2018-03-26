# SVG基本形状

SVG中插入一个图形，可以使用对应的标签。不同的元素使用不同的标签，可以使用属性定义大小和位置。

* 矩形 <rect> (point(x,y),(width,height),radius(rx,ry))
* 圆形 <circle> (point(cx,cy),r)
* 椭圆 <ellipse> (point(cx,cy),(rx,ry))
* 直线 <line> (point(x1,y1),point(x2,y2))
* 折线 <polyline> ([point(x1,y1)])
* 多边形 <polygon> ([point(x1,y1)])
* 路径 <path> (d=[M L]...)

<svg width="200" height="250" version="1.1" xmlns="http://www.w3.org/2000/svg">

  <rect x="10" y="10" width="30" height="30" stroke="black" fill="transparent" stroke-width="5"/>
  <rect x="60" y="10" rx="10" ry="10" width="30" height="30" stroke="black" fill="transparent" stroke-width="5"/>

  <circle cx="25" cy="75" r="20" stroke="red" fill="transparent" stroke-width="5"/>
  <ellipse cx="75" cy="75" rx="20" ry="5" stroke="red" fill="transparent" stroke-width="5"/>

  <line x1="10" x2="50" y1="110" y2="150" stroke="orange" fill="transparent" stroke-width="5"/>
  <polyline points="60 110 65 120 70 115 75 130 80 125 85 140 90 135 95 150 100 145"
      stroke="orange" fill="transparent" stroke-width="5"/>

  <polygon points="50 160 55 180 70 180 60 190 65 205 50 195 35 205 40 190 30 180 45 180"
      stroke="green" fill="transparent" stroke-width="5"/>

  <path d="M20,230 Q40,205 50,230 T90,230" fill="none" stroke="blue" stroke-width="5"/>
</svg>

### 矩形
rect标签会在屏幕上绘制一个矩形，(x,y)表示矩形左上角点的位置，(width,height)矩形的宽和长
(rx,ry)x方向和y方向上的圆角。

### 圆形
circle元素会在屏幕上绘制一个圆形,(cx,cy)圆心的位置，r圆的半径

### 椭圆
ellipse标签会在屏幕上绘制一个椭圆，(rx,ry)椭圆的两个半径,(cx,cy)椭圆中心的位置

### 线条
line标签绘制直线，(x1,y1)起点位置,(x2,y2)终点位置

### 折线
polyline标签绘制折线，折线是一组点放在一个points属性中。每个点必须包含2个数字，一个是x坐标，一个是y坐标。所以点列表 (0,0), (1,1) 和(2,2)可以写成这样：“0 0, 1 1, 2 2”

### 多边形
polygon是一个闭合的polyline.

### 路径
path是SVG基本形状中最强大的一个，它不仅能创建其他基本形状，还能创建更多其他形状

|指令 | 参数 | 名称 | 描述 |
|-----|----|------|------|
|  M  |(x,y)|moveto|移动画笔到(x,y)位置，不绘制 |
|  m  |(x,y)|moveto|同上，使用相对坐标 |
|  L  |(x,y)|lineto|从当前画笔所在位置绘制一条直线到指定的（x,y）坐标 |
|  l  |(x,y)|lineto|同上，使用相对坐标 |
|  H  |x|horizontal lineto|绘制一条水平直线到参数指定的x坐标点，y坐标为画笔的y坐标 |
|  h  |x|horizontal lineto|同上，使用相对坐标 |
|  V  |y|vertical lineto|从当前位置绘制一条垂直直线到参数指定的y坐标 |
|  v  |y|vertical lineto|同上，使用相对坐标 |
|  C  |x1,y1 x2,y2 x,y|curveto|从当前画笔位置绘制一条三次贝兹曲线到参数（x,y）指定的坐标。x1，y1和x2,y2是曲线的开始和结束控制点，用于控制曲线的弧度 |
|  c  |x1,y1 x2,y2 x,y|curveto|同上，使用相对坐标 |
|  S  |x2,y2 x,y|shorthand|从当前画笔位置绘制一条三次贝塞尔曲线到参数（x,y）指定的坐标。x2,y2是结束控制点。开始控制点和前一条曲线的结束控制点相同|
|  s  |x2,y2 x,y|shorthand|同上，使用相对坐标 |
|  Q  |x1,y1 x,y|二次方贝塞尔曲线|从当前画笔位置绘制一条二次方贝塞尔曲线到参数（x,y）指定的坐标。x1,y1是控制点，用于控制曲线的弧度|
|  q  |x1,y1 x,y|二次方贝塞尔曲线|同上，使用相对坐标 |
|  T  |x,y|平滑的二次贝塞尔曲线|从当前画笔位置绘制一条二次贝塞尔曲线到参数（x,y）指定的坐标。控制点被假定为最后一次使用的控制点|
|  t  |x,y|平滑的二次贝塞尔曲线|同上，使用相对坐标 |
|  A  |rx,ry x-axis-rotation large-arc-flag,sweepflag x,y|椭圆弧线|从当前画笔位置开始绘制一条椭圆弧线到（x,y）指定的坐标。rx和ry分别为椭圆弧线水平和垂直方向上的半径。x-axis-rotation指定弧线绕x轴旋转的度数。它只在rx和ry的值不相同时有效果。large-arc-flag是大弧标志位，取值0或1，用于决定绘制大弧还是小弧。sweep-flag用于决定弧线绘制的方向|
|  a  |rx,ry x-axis-rotation large-arc-flag,sweepflag x,y|椭圆弧线|同上，使用相对坐标 |
|  Z  |无|闭合路径|从结束点绘制一条直线到开始点，闭合路径|
|  z  |无|闭合路径|同上|

```xml
<svg width="500px" height="200px" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <path d="M10 10 L10 90" fill="none" stroke="green" stroke-width="5"/>
  <path d="M10 90 L 30 10" fill="none" stroke="red" stroke-width="4"/>
  <path d="M30 10 H 60 V 90" fill="none" stroke="yellow" stroke-width="5"/>
  <path d="M60 90 C20 40, 40 20, 90 10" fill="transparent" stroke="orange" stroke-width="5"/>
  <path d="M90 10 S120 40 140 90" fill="transparent" stroke="green" stroke-width="5"/>
  <path d="M140 90 Q80 50 140 10" fill="transparent" stroke="red" stroke-width="4" />
  <path d="M140 10 Q140 50 180 90 T200 180" fill="transparent" stroke="yellow" stroke-width="4" />
  <path d="M240 50 A45 45 0 0 1 285 95 L285 50 Z" fill="green"/>
</svg>
```
<svg width="500px" height="200px" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <path d="M10 10 L10 90" fill="none" stroke="green" stroke-width="5"/>
  <path d="M10 90 L 30 10" fill="none" stroke="red" stroke-width="4"/>
  <path d="M30 10 H 60 V 90" fill="none" stroke="yellow" stroke-width="5"/>
  <path d="M60 90 C20 40, 40 20, 90 10" fill="transparent" stroke="orange" stroke-width="5"/>
  <path d="M90 10 S120 40 140 90" fill="transparent" stroke="green" stroke-width="5"/>
  <path d="M140 90 Q80 50 140 10" fill="transparent" stroke="red" stroke-width="4" />
  <path d="M140 10 Q140 50 180 90 T200 180" fill="transparent" stroke="yellow" stroke-width="4" />
  <path d="M240 50 A45 45 0 0 1 285 95 L285 50 Z" fill="green"/>
</svg>
