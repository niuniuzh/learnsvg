# SVG基础变形

svg中可以使用transform属性。

## 平移translate

translate元素移动一段距离(x,y)将图形移动到点(x,y)
```xml
<svg width="500" height="50" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="40" height="40" fill="green" transform="translate(90,10)" />
</svg>
```
<svg width="500" height="50" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="40" height="40" fill="green" transform="translate(90,10)" />
</svg>

## 旋转rotate,斜切skew,缩放scale
```xml
<svg width="800" height="160" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <rect x="60" y="0" fill="red" width="50" height="50" transform="rotate(45) scale(1.2)" />
  <rect x="200" y="0" fill="green" width="50" height="50" transform="skewX(45)" />
  <rect x="300" y="100" fill="yellow" width="50" height="50" transform="scale(0.5)" />
</svg>
```

<svg width="800" height="160" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <rect x="60" y="0" fill="red" width="50" height="50" transform="rotate(45) scale(1.2)" />
  <rect x="200" y="0" fill="green" width="50" height="50" transform="skewX(45)" />
  <rect x="300" y="100" fill="yellow" width="50" height="50" transform="scale(0.5)" />
</svg>

SVG允许你无缝嵌入别的svg元素。因此你可以利用内部svg元素的属性viewBox、属性width和属性height简单创建一个新的坐标系统。
```xml
<svg width="500" height="120" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <circle cx="180" cy="40" r="40" fill="yellow" >
  <svg width="100" height="100" viewBox="0 0 50 50">
    <rect x="10" y="5" width="50" height="50" fill="#ff00ff"/>
  </svg>
</svg>
```

<svg width="500" height="120" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <circle cx="180" cy="40" r="40" fill="yellow" >
  <svg width="100" height="100" viewBox="0 0 50 50">
    <rect x="10" y="5" width="50" height="50" fill="#ff00ff"/>
  </svg>
</svg>
