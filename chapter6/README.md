# SVG文字文本

在一个SVG文档中，<text>元素内部可以放任何的文字。
<svg width="300" height="20" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <text x="180" y="15" fill="red" text-anchor="middle" stroke="green" stroke-width="1">Hello, World！</text>
</svg>

## text子元素tspan

tspan必须是一个text元素或别的tspan元素的子元素。tspan中,(x,y)是绝对坐标，(dx,dy)是相对坐标。rotate把所有的字符旋转一个角度。

<svg width="500" height="150" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <text x="10" y="15" transform="rotate(20 40, 30)">
    Hello, Everybody!
    <tspan dx="20" font-weight="bold" fill="red" >This is bold and red</tspan>
    Ok,thank you!
  </text>
</svg>

## text引用use
use元素允许引用已经定义的文本，高效地把它复制到当前位置。

<svg width="500" height="30" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <text id="example" fill="green">This is an example text.</text>
  <use xlink:href="#example" x="10" y="15" />
</svg>

## text文本路径textPath

该元素利用它的xlink:href属性取得一个任意路径，把字符对齐到路径，于是字体会环绕路径、顺着路径走：
<svg width="100%" height="100%" viewBox="0 0 1000 300"
     xmlns="http://www.w3.org/2000/svg" 
     xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <path id="MyPath"
          d="M 100 200 
             C 200 100 300   0 400 100
             C 500 200 600 300 700 200
             C 800 100 900 100 900 100" />
  </defs>

  <use xlink:href="#MyPath" fill="none" stroke="red"  />

  <text font-family="Verdana" font-size="45">
    <textPath xlink:href="#MyPath">
      我先往上去，然后往下去，然后再往上去，漂亮吧！
    </textPath>
  </text>

  <!-- Show outline of the viewport using 'rect' element -->
  <rect x="1" y="1" width="998" height="298"
        fill="none" stroke="black" stroke-width="2" />
</svg>
