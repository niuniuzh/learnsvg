# SVG 简介

SVG，是W3C XML的分支语言之一，用于标记可缩放的矢量图形。SVG 是用XML格式定义的矢量图。

## SVG是什么?
* SVG 表示可缩放矢量图
* SVG 用来定义WEB上使用的矢量图
* SVG 用XML格式定义矢量图
* SVG 在缩放时不会损失任何的图片质量
* SVG 文件里的所有元素和属性都可以运用动画效果
* SVG 是W3C推荐的
* SVG 集成了其它W3C标准，比如 DOM 和 XSL

## SVG优势
* SVG 图片可以使用文本编辑器创建和编辑
* SVG 图片能够实现内容搜索，索引，脚本控制和压缩
* SVG 图片是可缩放的
* SVG 图片可以以任意高分辨率打印
* SVG 图片的缩放显示是无损的
* SVG 是开放标准
* SVG 文件是纯XML的

## 创建SVG流程

```xml
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">

  <rect width="100%" height="100%" fill="red" />
</svg>
```
从svg根元素开始：
* 舍弃来自(X)HTML的doctype声明，因为基于SVG的DTD验证导致的问题比它能解决的问题更多。
* 添加version和baseProfile属性，供其它类型的验证方式确定SVG版本。
* 绘制一个完全覆盖图像区域的矩形 <rect/>，把背景颜色设为红色。
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">

  <rect width="100%" height="100%" fill="red" />
</svg>
