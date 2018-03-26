# SVG滤镜简介

SVG滤镜是用来对SVG图像添加一些特殊效果。

在SVG里，一共有下面这些滤镜:
* feBlend
* feColorMatrix – 颜色变换
* feComponentTransfer
* feComposite
* feConvolveMatrix
* feDiffuseLighting
* feDisplacementMap
* feFlood
* feGaussianBlur
* feImage
* feMerge
* feMorphology
* feOffset – 阴影效果
* feSpecularLighting
* feTile
* feTurbulence
* feDistantLight – 灯光效果
* fePointLight – 灯光效果
* feSpotLight – 灯光效果

所有的SVG滤镜元素都需要定义在defs标记内。filter标记用来定义SVG滤镜。filter标记需要一个id属性，
它是这个滤镜的标志。SVG图形使用这个id来引用滤镜。

## 模糊虑镜
两个SVG圆形，右边的一样使用了模糊特效：
<svg width="230" height="120" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">

  <filter id="blurMe">
    <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
  </filter>

  <circle cx="60"  cy="60" r="50" fill="green" />

  <circle cx="170" cy="60" r="50" fill="green" filter="url(#blurMe)" />
</svg>

id属性定义了这个滤镜的唯一标志
使用feGaussianBlur标记定义模糊效果
stdDeviation属性定义了模糊的程度
```xml
<svg width="230" height="120" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">

  <filter id="blurMe">
    <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
  </filter>

  <circle cx="60"  cy="60" r="50" fill="green" />

  <circle cx="170" cy="60" r="50" fill="green" filter="url(#blurMe)" />
</svg>
```

## 颜色滤镜feColorMatrix

feColorMatrix过滤器可以根据颜色矩阵来修改目标图形的色彩效果.每一个像素的颜色值(使用[R,G,B,A]矢量表示)乘以矩阵获得新的颜色值。
feColorMatrix标记里的type属性的值可以是matrix | saturate | hueRotate | luminanceToAlpha。


<svg width="100%" height="100%" viewBox="0 0 150 360"
 preserveAspectRatio="xMidYMid meet"
 xmlns="http://www.w3.org/2000/svg"
 xmlns:xlink="http://www.w3.org/1999/xlink">

  <text x="70" y="50">原图效果</text>
  <g>
    <circle cx="30" cy="30" r="20" fill="blue" fill-opacity="0.5" />
    <circle cx="20" cy="50" r="20" fill="green" fill-opacity="0.5" />
    <circle cx="40" cy="50" r="20" fill="red" fill-opacity="0.5" />
  </g>


  <text x="70" y="120">type="matrix"</text>

  <filter id="colorMeMatrix">
    <feColorMatrix in="SourceGraphic"
      type="matrix"
      values="0 0 0 0 0
              1 1 1 1 0
              0 0 0 0 0
              0 0 0 1 0" />
  </filter>

  <g filter="url(#colorMeMatrix)">
    <circle cx="30" cy="100" r="20" fill="blue"  fill-opacity="0.5" />
    <circle cx="20" cy="120" r="20" fill="green" fill-opacity="0.5" />
    <circle cx="40" cy="120" r="20" fill="red"   fill-opacity="0.5" />
  </g>


  <text x="70" y="190">type="saturate"</text>

  <filter id="colorMeSaturate">
    <feColorMatrix in="SourceGraphic"
      type="saturate"
      values="0.2" />
  </filter>

  <g filter="url(#colorMeSaturate)">
    <circle cx="30" cy="170" r="20" fill="blue" fill-opacity="0.5" />
    <circle cx="20" cy="190" r="20" fill="green" fill-opacity="0.5" />
    <circle cx="40" cy="190" r="20" fill="red" fill-opacity="0.5" />
  </g>


  <text x="70" y="260">type="hueRotate"</text>

  <filter id="colorMeHueRotate">
    <feColorMatrix in="SourceGraphic"
      type="hueRotate"
      values="180" />
  </filter>

  <g filter="url(#colorMeHueRotate)">
    <circle cx="30" cy="240" r="20" fill="blue"  fill-opacity="0.5" />
    <circle cx="20" cy="260" r="20" fill="green" fill-opacity="0.5" />
    <circle cx="40" cy="260" r="20" fill="red"   fill-opacity="0.5" />
  </g>


  <text x="70" y="320">type="luminanceToAlpha"</text>

  <filter id="colorMeLTA">
    <feColorMatrix in="SourceGraphic"
      type="luminanceToAlpha" />
  </filter>

  <g filter="url(#colorMeLTA)">
    <circle cx="30" cy="310" r="20" fill="blue"  fill-opacity="0.5" />
    <circle cx="20" cy="330" r="20" fill="green" fill-opacity="0.5" />
    <circle cx="40" cy="330" r="20" fill="red"   fill-opacity="0.5" />
  </g>
</svg>

## 光照滤镜feDiffuseLighting

标记的作用是产生光照效果滤镜，它使用原图的alpha通道作为纹理图，输出的结果取决于光线颜色，光源位置和图片的物体表面纹理。

<svg width="440" height="140" xmlns="http://www.w3.org/2000/svg">

  <!-- No light is applied -->
  <text text-anchor="middle" x="60" y="22">原图</text>
  <circle cx="60" cy="80" r="50" fill="green" />

  <!-- the light source is a fePointLight element -->
  <text text-anchor="middle" x="170" y="22">点状光</text>
  <filter id="lightMe1">
    <feDiffuseLighting in="SourceGraphic" result="light" lighting-color="white">
      <fePointLight x="150" y="60" z="20" />
    </feDiffuseLighting>

    <feComposite in="SourceGraphic" in2="light"
                 operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>
  </filter>

  <circle cx="170" cy="80" r="50" fill="green" filter="url(#lightMe1)" />

  <!-- the light source is a feDistantLight element -->
  <text text-anchor="middle" x="280" y="22">平行光</text>
  <filter id="lightMe2">
    <feDiffuseLighting in="SourceGraphic" result="light" lighting-color="white">
      <feDistantLight azimuth="240" elevation="20"/>
    </feDiffuseLighting>

    <feComposite in="SourceGraphic" in2="light"
                 operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>
  </filter>

  <circle cx="280" cy="80" r="50" fill="green" filter="url(#lightMe2)" />

  <!-- the light source is a feSpotLight source -->
  <text text-anchor="middle" x="390" y="22">聚光</text>
  <filter id="lightMe3">
    <feDiffuseLighting in="SourceGraphic" result="light" lighting-color="white">
      <feSpotLight x="360" y="5" z="30" limitingConeAngle="20"
                   pointsAtX="390" pointsAtY="80" pointsAtZ="0"/>
    </feDiffuseLighting>

    <feComposite in="SourceGraphic" in2="light"
                 operator="arithmetic" k1="1" k2="0" k3="0" k4="0"/>
  </filter>

  <circle cx="390" cy="80" r="50" fill="green" filter="url(#lightMe3)" />
</svg>
