# SVG基本属性

上一节介绍了基本的图形，这节介绍基本的属性,怎么给目标上色填充。以及如何使用内联CSS样式。

## stroke属性
stroke属性定义了给定图形元素的外轮廓的颜色。它的默认值是none。可以使用颜色名，rgba值。
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
 <path stroke="#ff0000" d="M5 20 1215 20" />
 <path stroke="green" d="M5 30 1215 30" />
</svg>

## stroke-linecap属性 
在开放子路径被设置描边的情况下，用于开放自路径两端的形状.butt | round | square | inherit
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
  <line stroke-linecap="butt" x1="30" y1="30" x2="30" y2="90" stroke="black" stroke-width="20"/>
  <line stroke-linecap="round" x1="60" y1="30" x2="60" y2="90" stroke="black" stroke-width="20"/>
  <line stroke-linecap="square" x1="90" y1="30" x2="90" y2="90" stroke="black" stroke-width="20"/>
</svg>

## stroke-width
属性指定了当前对象的轮廓的宽度。它的默认值是1。
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
  <line x1="30" y1="30" x2="30" y2="90" stroke-width="20" stroke="red"/>
  <line x1="60" y1="30" x2="60" y2="90" stroke-width="20%" stroke="yellow"/>
  <line x1="90" y1="30" x2="90" y2="90" stroke-width="20" stroke="blue"/>
</svg>

# stroke-dasharray&&stroke-dashoffset
stroke-dasharray可控制用来描边的点划线的图案范式,stroke-dasharray属性的参数，是一组用逗号分割的数字组成的数列。
stroke-dashoffset 属性指定了dash模式到路径开始的距离。
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
  <path d="M 10 75 Q 50 10 100 75 T 190 75" stroke="black" stroke-linecap="round" stroke-dasharray="5,10,5" fill="none"/>
  <path d="M 10 75 L 190 75" stroke="red" stroke-dashoffset="80" stroke-linecap="round" stroke-width="1" stroke-dasharray="5,5" fill="none"/>
</svg>

## stroke-linejoin
stroke-linejoin属性，用来控制两条描边线段之间，用什么方式连接.
<svg width="160" height="280" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <polyline points="40 60 80 20 120 60" stroke="black" stroke-width="20" stroke-linecap="butt" fill="none" stroke-linejoin="miter"/>
  <polyline points="40 140 80 100 120 140" stroke="black" stroke-width="20" stroke-linecap="round" fill="none" stroke-linejoin="round"/>
  <polyline points="40 220 80 180 120 220" stroke="black" stroke-width="20" stroke-linecap="square" fill="none" stroke-linejoin="bevel"/>
</svg>

## fill属性
设置对象内部的颜色
```xml
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
     <rect x="0" y="0" width="100" height="100" fill="green" />
</svg>
```
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
     <rect x="0" y="0" width="100" height="100" fill="green" />
</svg>

## 使用CSS
可以通过CSS来样式化填充和描边。语法和在html里使用CSS一样，只不过你要把background-color、border改成fill和stroke。
```xml
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <style type="text/css"><![CDATA[
       #MyRect {
         stroke: black;
         fill: red;
       }
       #MyRect:hover {
   stroke: black;
   fill: blue;
 }
    ]]></style>
  </defs>
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>
```
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <style type="text/css"><![CDATA[
       #MyRect {
         stroke: black;
         fill: red;
       }
       #MyRect:hover {
   stroke: black;
   fill: blue;
 }
    ]]></style>
  </defs>
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>
