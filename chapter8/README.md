# SVG剪切和遮罩

## clip-path剪切路径

SVG中clipPath，用来定义剪裁路径的。clipPath用来移除在别处定义的元素的部分内容。

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs><!-- 定义 -->
    <clipPath id="clipPath"><!-- 定义剪裁路径 -->
        <rect x="0" y="0" width="80" height="80" /><!-- 路径详细 -->
    </clipPath>
  </defs>
  <circle cx="160" cy="60" r="50" fill="#34538b" clip-path="url(#clipPath)" />
  <defs>
    <clipPath id="cut-off-bottom">
      <rect x="0" y="0" width="200" height="100" />
    </clipPath>
  </defs>

  <circle cx="100" cy="100" r="100" clip-path="url(#cut-off-bottom)" />
</svg>

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
<defs>
    <clipPath id="clipPath5">
        <text x="10" y="20" style="font-size: 20px; ">This is a text</text>
    </clipPath>
</defs>

<g style="clip-path: url(#clipPath5);">
    <rect x="5" y="5" width="190" height="90"

          style="stroke: none; fill:#00ff00;"/>
    <circle cx="20" cy="20" r="20" style="stroke: none; fill: #ff0000;" />
</g>
</svg>


## 遮罩

可以使用SVG图形作为遮罩，下面是一个遮罩的例子：

<svg>
  <defs>
    <mask id="mask2" x="0" y="0" width="100" height="100" >
      <circle cx="35" cy="35" r="25" style="stroke:none; fill: #ffffff"/>
    </mask>
  </defs>

  <rect x="1" y="1" width="100" height="100"
    style="stroke: none; fill: #0000ff; mask: url(#mask2)"/>

</svg>

遮罩的效果最令人印象深刻的是表现为一个渐变

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <linearGradient id="Gradient">
      <stop offset="0" stop-color="white" stop-opacity="0" />
      <stop offset="1" stop-color="white" stop-opacity="1" />
    </linearGradient>
    <mask id="Mask">
      <rect x="0" y="0" width="200" height="200" fill="url(#Gradient)"  />
    </mask>
  </defs>

  <rect x="0" y="0" width="200" height="200" fill="green" />
  <rect x="0" y="0" width="200" height="200" fill="red" mask="url(#Mask)" />
</svg>
