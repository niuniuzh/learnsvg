# SVG渐变色

渐变色是指从一种颜色平滑的过渡到另外一种颜色。线性渐变色 Linear
辐射式(放射式)渐变色 Radial.

## 线性渐变

要插入一个线性渐变，你需要在SVG文件的defs元素内部，创建一个linearGradient。
```xml
<svg width="400" height="160" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <defs>
    <linearGradient id="grad2" x1="0" y1="0" x2="0" y2="1">
    <stop class="stop1" offset="0%"/>
    <stop class="stop2" offset="100%"/>
    </linearGradient>
    <style type="text/css"><![CDATA[#rect { fill: url(#grad2); }
      .stop1 { stop-color: yellow; }
      .stop2 { stop-color: red; }]]></style>
  </defs>
  <ellipse cx="200" cy="70" rx="85" ry="55" fill="url(#grad1)" />
  <rect id="rect" x="10" y="10" rx="15" ry="15" width="100" height="100"/>
</svg>
```
<svg width="400" height="160" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <defs>
    <linearGradient id="grad2" x1="0" y1="0" x2="0" y2="1">
    <stop class="stop1" offset="0%"/>
    <stop class="stop2" offset="100%"/>
    </linearGradient>
    <style type="text/css"><![CDATA[#rect { fill: url(#grad2); }
      .stop1 { stop-color: yellow; }
      .stop2 { stop-color: red; }]]></style>
  </defs>
  <ellipse cx="200" cy="70" rx="85" ry="55" fill="url(#grad1)" />
  <rect id="rect" x="10" y="10" rx="15" ry="15" width="100" height="100"/>
</svg>

linearGradient标记的id属性定义了这个渐变色的唯一标志,每种颜色都使用一个stop标记定义,offset指定位置,
stop-color用来指定颜色,stop-opacity透明度。渐变的方向可以通过两个点来控制，它们分别是属性x1、x2、y1和y2,
这些属性定义了渐变路线走向。fill属性定义了需要引用的渐变色的ID。将属性fill设置为url(#grad1)。


## 径向渐变

径向渐变与线性渐变相似，只是它是从一个点开始发散绘制渐变,创建径向渐变需要在文档的defs中添加一个radialGradient。

<svg width="520" height="240" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <defs>
      <radialGradient id="RadialGradient1" cx="0.5" cy="0.5" r="1">
        <stop offset="0%" stop-color="red" stop-opacity="0.8"/>
        <stop offset="100%" stop-color="yellow" stop-opacity="0.8"/>
      </radialGradient>
      <radialGradient id="RadialGradient2" cx="0.25" cy="0.25" r="0.25">
        <stop offset="0%" stop-color="red"/>
        <stop offset="100%" stop-color="blue"/>
      </radialGradient>
      <radialGradient id="GradientPad"
            cx="0.5" cy="0.5" r="0.4" fx="0.75" fy="0.75"
            spreadMethod="pad">
        <stop offset="0%" stop-color="red"/>
        <stop offset="100%" stop-color="blue"/>
      </radialGradient>
      <radialGradient id="GradientRepeat"
            cx="0.5" cy="0.5" r="0.4" fx="0.75" fy="0.75"
            spreadMethod="repeat">
        <stop offset="0%" stop-color="red"/>
        <stop offset="100%" stop-color="blue"/>
      </radialGradient>
      <radialGradient id="GradientReflect"
            cx="0.5" cy="0.5" r="0.4" fx="0.75" fy="0.75"
            spreadMethod="reflect">
        <stop offset="0%" stop-color="red"/>
        <stop offset="100%" stop-color="blue"/>
      </radialGradient>
  </defs>
  <circle cx="60" cy="60" r="45" fill="url(#RadialGradient1)"/> 
  <rect x="10" y="120" rx="15" ry="15" width="100" height="100" fill="url(#RadialGradient2)"/> 
  <rect x="190" y="10" rx="15" ry="15" width="100" height="100" fill="url(#GradientPad)"/>
  <rect x="190" y="120" rx="15" ry="15" width="100" height="100" fill="url(#GradientRepeat)"/>
  <rect x="320" y="120" rx="15" ry="15" width="100" height="100" fill="url(#GradientReflect)"/>

  <text x="195" y="30" fill="white" font-family="sans-serif" font-size="12pt">Pad</text>
  <text x="195" y="140" fill="white" font-family="sans-serif" font-size="12pt">Repeat</text>
  <text x="325" y="140" fill="white" font-family="sans-serif" font-size="12pt">Reflect</text>
</svg>

id属性定义了这个渐变色的唯一标志,每种颜色都使用一个stop标记定义,offset指定位置,
stop-color用来指定颜色,stop-opacity透明度。cx,cy,r控制渐变的中心点。fx和fy定义了焦点。
如果没有给出焦点，将认为该点与中心点的位置一致。spreadMethod属性控制了当渐变到达终点的行为，
但是此时该对象尚未被填充颜色。这个属性可以有三个值：pad、reflect或repeat。

