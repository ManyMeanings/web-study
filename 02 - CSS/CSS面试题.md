- [1. 介绍一下 CSS 的盒子模型？&#10084;](#1-介绍一下-css-的盒子模型)
- [2. CSS 选择器有哪些？](#2-css-选择器有哪些)
- [3. CSS 中哪些属性可以继承？](#3-css-中哪些属性可以继承)
- [4. CSS 优先级算法如何计算？&#10084;](#4-css-优先级算法如何计算)
- [5. 关于 a 标签伪类 LVHA 的解释?](#5-关于-a-标签伪类-lvha-的解释)
- [6. 如何居中 div?&#10084;](#6-如何居中-div)
- [7. display 有哪些值？说明它们的作用。](#7-display-有哪些值说明它们的作用)
- [8. position 的值 relative 和 absolute 定位原点是？&#10084;](#8-position-的值-relative-和-absolute-定位原点是)
- [9. CSS3 有哪些新特性？](#9-css3-有哪些新特性)
- [10. 请解释一下 Flexbox（弹性盒布局模型），以及适用场景？](#10-请解释一下-flexbox弹性盒布局模型以及适用场景)
- [11. 如何用纯 CSS 绘制一个三角形？](#11-如何用纯-css-绘制一个三角形)
- [12. 一个满屏品字布局如何设计？](#12-一个满屏品字布局如何设计)
- [13. `li`与`li`之间有看不见的空白间隔是什么原因引起的？有什么解决办法？](#13-li与li之间有看不见的空白间隔是什么原因引起的有什么解决办法)
- [14. `width: auto`和`width: 100%`的区别?](#14-width-auto和width-100的区别)
- [15. 简单介绍使用图片 base64 编码的优点和缺点。](#15-简单介绍使用图片-base64-编码的优点和缺点)
- [16. margin 重叠问题的理解。&#10084;](#16-margin-重叠问题的理解)
- [17. 对 BFC 规范（块级格式化上下文：block formatting context）的理解？&#10084;](#17-对-bfc-规范块级格式化上下文block-formatting-context的理解)
- [18. IFC（行级格式化上下文）是什么？](#18-ifc行级格式化上下文是什么)
- [19. CSS 优化、提高性能的方法有哪些？&#10084;](#19-css-优化提高性能的方法有哪些)
- [20. margin 和 padding 分别适合什么场景使用？](#20-margin-和-padding-分别适合什么场景使用)
- [21. 抽离样式模块怎么写，说出思路？](#21-抽离样式模块怎么写说出思路)
- [22. 什么是响应式设计？响应式设计的基本原理是什么？](#22-什么是响应式设计响应式设计的基本原理是什么)
- [23. 什么是视差滚动?](#23-什么是视差滚动)
- [24. 怎么让 Chrome 支持小于 12px 的文字？](#24-怎么让-chrome-支持小于-12px-的文字)
- [25. font-style 属性中 italic 和 oblique 的区别？](#25-font-style-属性中-italic-和-oblique-的区别)
- [26. 设备像素、css 像素、设备独立像素、dpr、ppi 之间的区别？](#26-设备像素css-像素设备独立像素dprppi-之间的区别)
- [27. layoutviewport、visualviewport 和 idealviewport 的区别？](#27-layoutviewportvisualviewport-和-idealviewport-的区别)
- [28. `position:fixed`在 Android 下无效怎么处理？](#28-positionfixed在-android-下无效怎么处理)
- [29. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？](#29-如果需要手动写动画你认为最小时间间隔是多久为什么)
- [30. png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过 webp？&#128128;](#30-pngjpggif-这些图片格式解释一下分别什么时候用有没有了解过-webp)
- [31. 什么是 CSS 预处理器/后处理器？](#31-什么是-css-预处理器后处理器)
- [32. 阐述一下 CSSSprites](#32-阐述一下-csssprites)
- [33. transition 和 animation 的区别](#33-transition-和-animation-的区别)
- [34. min-width/max-width 和 min-height/max-height 属性间的覆盖规则？](#34-min-widthmax-width-和-min-heightmax-height-属性间的覆盖规则)
- [35. 什么是替换元素？](#35-什么是替换元素)
- [36. `margin: auto` 的填充规则？](#36-margin-auto-的填充规则)
- [37. margin 无效的情形?](#37-margin-无效的情形)
- [38. line-height 的特殊性？](#38-line-height-的特殊性)
- [39. overflow 的特殊性？](#39-overflow-的特殊性)
- [40. 什么是层叠上下文？&#10084;](#40-什么是层叠上下文)
- [41. 如何实现单行/多行文本溢出的省略？](#41-如何实现单行多行文本溢出的省略)
- [42. 常见的元素隐藏方式？](#42-常见的元素隐藏方式)
- [43. 主流浏览器内核私有属性 css 前缀？](#43-主流浏览器内核私有属性-css-前缀)
- [44. css reset 和 normalize.css 有什么区别？](#44-css-reset-和-normalizecss-有什么区别)
- [45. offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别？](#45-offsetwidthoffsetheightclientwidthclientheight-与-scrollwidthscrollheight-的区别)

### 1. 介绍一下 CSS 的盒子模型？&#10084;

CSS 盒子模型分为标准盒模型和 IE 盒模型，它们都由内容、内边距、边框和外边距组成。标准盒模型和 IE 盒模型的区别在于设置 width 和 height 时，所对应的范围不同。标准盒模型的 width 和 height 属性的范围只包含 content，而 IE 盒模型 width 和 height 属性的范围包含了 border、padding 和 content。

我们可以通过修改元素的 box-sizing 属性来改变元素的盒模型。

### 2. CSS 选择器有哪些？

1. id 选择器（#myid）
2. 类选择器（.myclassname）
3. 标签选择器（div）
4. 后代选择器（h1 p）
5. 相邻后代（子）选择器（ul>li）
6. 兄弟选择器（li~a）
7. 相邻兄弟选择器（li+a）
8. 属性选择器（a[rel="external"]）
9. 伪类选择器（a:hover）
10. 伪元素选择器（::before）
11. 通配符选择器（\*）

### 3. CSS 中哪些属性可以继承？

一般具有继承性的属性有，**字体相关的属性**，font-size 和 font-weight 等。**文本相关的属性**，color 和 text-align 等。**表格的一些布局属性**、**列表属性**如 list-style 等。还有**光标属性** cursor、**元素可见性** visibility。

当一个属性不是继承属性的时候，我们也可以通过将它的值设置为 inherit 来使它从父元素那获取同名的属性值来继承。

### 4. CSS 优先级算法如何计算？&#10084;

选择器的特殊性值分为三个等级，如下：

1. id 选择器 x,0,0
2. 类选择器/属性选择器/伪类选择器 0,x,0
3. 标签选择器/伪元素选择器 0,0,x

计算规则：

1. 每个等级的值为选择器出现次数相加，不可进位。
2. 大小比较从左向右，如果某一位数值相同，则判断下一位数值。
3. !important（权重），它没有特殊性值，但它的优先级是最高的。
4. 如果两个选择器优先级相同，则最后出现的优先级高，!important 也适用。
5. 继承样式优先级最低，通配符样式优先级高于继承样式，为 0,0,0
6. CSS 样式表的冲突：相同选择器采取就近原则，外部样式表的 id 选择器 > 内嵌样式表的标签选择器。

### 5. 关于 a 标签伪类 LVHA 的解释?

a 标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类 :link、:visited、:hover、:active

当链接未访问过时，当鼠标滑过 a 链接时，满足 :link 和 :hover 两种状态，要改变 a 标签的颜色，就必须将 :hover 伪类在 :link 伪类后面声明。当鼠标点击激活 a 链接时，同时满足 :link、:hover、:active 三种状态，要显示 a 标签激活时的样式，必须将 :active 声明放到 :link 和 :hover 之后，因此得出 LVHA 这个顺序。其他情况同理。

### 6. 如何居中 div?&#10084;

```css
/*水平居中*/

/*1. 给 div 设置一个宽度，然后添加 margin: 0 auto*/
div {
  width: 200px;
  margin: 0 auto;
}

/*2. 利用 text-align: center 实现*/
.container {
  text-align: center;
}

div {
  display: inline-block;
  width: 200px;
  height: 200px;
  background-color: red;
}

/*水平垂直居中*/

/*1. 利用绝对定位，设置四个方向的值都为0，并将 margin 设置为 auto */
div {
  position: absolute;
  width: 200px;
  height: 200px;
  margin: auto;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: red;
}

/*2. 利用绝对定位，确定容器的宽高，先将元素的左上角定位到页面的中心，然后再通过 margin 来调整元素的中心点到页面的中心。*/
div {
  position: absolute;
  width: 500px;
  height: 300px;
  top: 50%;
  left: 50%;
  margin: -150px 0 0 -250px;
  background-color: red;
}

/*3. 利用绝对定位,未知容器的宽高，利用 transform 属性*/
div {
  position: absolute; /*相对定位或绝对定位均可*/
  width: 500px;
  height: 300px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: red;
}

/*4. 利用flex布局*/
.container {
  display: flex;
  align-items: center;
  justify-content: center;
}

div {
  width: 100px;
  height: 100px;
  background-color: red;
}
```

### 7. display 有哪些值？说明它们的作用。

- `block` 块类型，默认宽度为父元素宽度，可设置宽高，换行显示。
- `none` 元素不显示，并从文档流中移除。
- `inline` 行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
- `inline-block` 默认宽度为内容宽度，可以设置宽高，同行显示。
- `list-item` 像块类型元素一样显示，并添加样式列表标记。
- `table` 此元素会作为块级表格来显示。
- `inherit` 规定应该从父元素继承 display 属性的值。

### 8. position 的值 relative 和 absolute 定位原点是？&#10084;

relative 相对于其元素本身所在正常位置进行定位,设置偏移仍然占用原来的文档空间。

absolute 定位原点是离自己最近的非 static 祖先元素（到 html 根标签为止）的左上角为原点，设置偏移后元素原先在正常文档流中所占的空间会关闭，就像元素原来不存在一样。

### 9. CSS3 有哪些新特性？

- 新增各种 CSS 选择器 （:not(.input)：所有 class 不是“input”的节点）
- 圆角 （border-radius: 8px）
- 多列布局 （multi-columnlayout）
- 阴影和反射 （shadow\reflect）
- 文字特效 （text-shadow）
- 文字渲染 （text-decoration）
- 线性渐变 （gradient）
- 缩放，旋转，定位，倾斜，动画，多背景（transform）

### 10. 请解释一下 Flexbox（弹性盒布局模型），以及适用场景？

flex 布局是 CSS3 新增的一种布局方式，我们可以通过将一个元素的 display 属性值设置为 flex 从而使它成为一个 flex 容器，它的所有子元素都会成为它的项目。

一个容器默认有两条轴，一个是水平的主轴，一个是与主轴垂直的交叉轴。我们可以使用 flex-direction 来指定主轴的方向。我们可以使用 justify-content 来指定元素在主轴上的排列方式，使用 align-items 来指定元素在交叉轴上的排列方式。还可以使用 flex-wrap 来规定当一行排列不下时的换行方式。

对于容器中的项目，我们可以使用 order 属性来指定项目的排列顺序，还可以使用 flex-grow 来指定当排列空间有剩余的时候，项目的放大比例。还可以使用 flex-shrink 来指定当排列空间不足时，项目的缩小比例。align-self 属性允许单个项目有与其他项目不一样的对齐方式。

### 11. 如何用纯 CSS 绘制一个三角形？

相邻边框连接处的均分原理。将元素宽高设置为 0，只设置 border，隐藏三条边，剩下的的就是一个三角形。

```css
#demo {
  width: 0;
  height: 0;
  border-width: 20px;
  border-style: solid;
  border-color: transparent transparent red transparent;
}
```

### 12. 一个满屏品字布局如何设计？

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>满屏品字布局</title>
    <style type="text/css">
      * {
        margin: 0;
        padding: 0;
      }

      html,
      body {
        height: 100%; /*此设置非常关键，因为默认的body，HTML高度为0*/
      }

      .header {
        height: 50%;
        width: 50%;
        background: #ccc;
        margin: 0 auto;
      }

      .main {
        width: 100%;
        height: 50%;
      }

      .main .left,
      .main .right {
        float: left; /*采用float方式，对元素进行左右定位*/
        width: 50%; /*此步解决元素相对窗口的定位问题*/
        height: 100%; /*此步解决元素相对窗口的定位问题*/
        background: yellow;
      }

      .main .right {
        background: green;
      }
    </style>
  </head>
  <body>
    <div class="header"></div>
    <div class="main">
      <div class="left"></div>
      <div class="right"></div>
    </div>
  </body>
</html>
```

### 13. `li`与`li`之间有看不见的空白间隔是什么原因引起的？有什么解决办法？

浏览器会把 inline 元素间的空白字符（空格、换行、Tab 等）渲染成一个空格。而为了美观。我们通常是一个`<li>`放在一行，这导致`<li>`换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。

解决方法：设置浮动；将所有`<li>`写在同一行；将`<ul>`字符大小设为 0。

### 14. `width: auto`和`width: 100%`的区别?

`width: 100%`会使元素 box 的宽度等于父元素的 contentbox 的宽度,并且随着父级的宽度自动变化，增加子元素的`padding`和`margin`之后，它的 contentbox 还是不变的。

`width:auto`会使元素撑满整个父元素，`margin`、`border`、`padding`、`content`区域会自动分配水平空间。

一般`width:auto`使用的多，因为这样灵活，而`width:100%`使用比较少，因为在增加`padding`或者`margin`的时候，容易使其突破父级框，破环布局。

### 15. 简单介绍使用图片 base64 编码的优点和缺点。

base64 编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的 url 属性。

优点：少一个图片的 HTTP 请求。

缺点：编码后的大小会比原文件大小大 1/3；无法直接缓存；兼容性的问题（ie8+）

### 16. margin 重叠问题的理解。&#10084;

margin 重叠指的是标准文档流中，竖直方向的 margin 不叠加，只取较大的值作为 margin 。

一般来说可以分为四种情形：

第一种是相邻兄弟元素的 marin-bottom 和 margin-top 的值发生重叠。这种情况下我们可以通过设置其中一个元素为 BFC 来解决。

第二种是父元素的 margin-top 和子元素的 margin-top 发生重叠。它们发生重叠是因为它们是相邻的，所以我们可以通过这一点来解决这个问题。我们可以为父元素设置 border-top、padding-top 值来分隔它们，当然我们也可以将父元素设置为 BFC 来解决。

第三种是高度为 auto 的父元素的 margin-bottom 和子元素的 margin-bottom 发生重叠。它们发生重叠一个是因为它们相邻，一个是因为父元素的高度不固定。因此我们可以为父元素设置 border-bottom、padding-bottom 来分隔它们，也可以为父元素设置一个高度，max-height 和 min-height 也能解决这个问题。当然将父元素设置为 BFC 是最简单的方法。

第四种情况，是没有内容的元素，自身的 margin-top 和 margin-bottom 发生的重叠。我们可以通过为其设置 border、padding 或者高度来解决这个问题。

### 17. 对 BFC 规范（块级格式化上下文：block formatting context）的理解？&#10084;

BFC 指的是块级格式化上下文，一个元素形成了 BFC 之后，那么它内部元素产生的布局不会影响到外部元素，外部元素的布局也不会影响到 BFC 中的内部元素。一个 BFC 就像是一个隔离区域，和其他区域互不影响。

特点：

- BFC 内部的子元素，在垂直方向，边距会发生重叠。
- BFC 在页面中是独立的容器，外面的元素不会影响里面的元素，反之亦然。
- BFC 区域不与旁边的 float box 区域重叠。（可以用来清除浮动带来的影响）。
- 在计算 BFC 的高度时，子元素的 float box 也会参与计算。

BFC 元素：

- overflow: 不为 visible，可以让属性是 hidden、auto。
- 浮动元素 float ＝ left|right 或 inherit（≠none）
- 绝对定位元素 position ＝ absolute 或 fixed
- display ＝ inline-block|flex|inline-flex|table-cell 或 table-caption

### 18. IFC（行级格式化上下文）是什么？

IFC 指的是行级格式化上下文，它有这样的一些布局规则：

- 行级上下文内部的盒子会在水平方向，一个接一个地放置。
- 当一行不够的时候会自动切换到下一行。
- 行级上下文的高度由内部最高的内联盒子的高度决定。

### 19. CSS 优化、提高性能的方法有哪些？&#10084;

加载性能：

- css 压缩：将写好的 css 进行打包压缩，可以减少很多的体积。
- 减少使用 @import,而建议使用 link，因为后者在页面加载时一起加载，前者是等待页面加载完成之后再进行加载。

选择器性能：

- 过滤掉无关的规则，这样样式系统就不会浪费时间去匹配它们了。
- 避免使用通配规则，只对需要用到的元素进行选择。
- 尽量少的去对标签进行选择，而是用 class。
- 尽量少的去使用后代选择器。后代选择器的开销是最高的，尽量将选择器的深度降到最低，最高不要超过三层。
- 了解哪些属性是可以通过继承而来的，然后避免对这些属性重复指定规则。

渲染性能：

- 慎重使用高性能属性：浮动、定位。
- 尽量减少页面重排、重绘。
- 属性值为 0 时，不加单位。
- css 雪碧图，同一页面相近部分的小图标，方便使用，减少页面的请求次数，但是同时图片本身会变大，使用时，优劣考虑清楚，再使用。
- 不滥用 web 字体。webfonts 通常体积庞大，而且一些浏览器在下载 webfonts 时会阻塞页面渲染损伤性能。

可维护性：

- 将具有相同属性的样式抽离出来，整合并通过 class 在页面中进行使用，提高 css 的可维护性。
- 样式与内容分离：将 css 代码定义到外部 css 中。

### 20. margin 和 padding 分别适合什么场景使用？

margin 是用来隔开元素与元素的间距；padding 是用来隔开元素与内容的间隔。margin 用于布局分开元素使元素与元素互不相干。padding 用于元素与内容之间的间隔，让内容（文字）与（包裹）元素之间有一段距离。

### 21. 抽离样式模块怎么写，说出思路？

把常用的 css 样式单独做成 css 文件。通用的和业务相关的分离出来，通用的做成样式模块共享，业务相关的，放进业务相关的库里面做成对应功能的模块。

### 22. 什么是响应式设计？响应式设计的基本原理是什么？

响应式网站设计是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。基本原理是通过媒体查询检测不同的设备屏幕尺寸做处理。页面头部必须有 meta 声明的 viewport。

### 23. 什么是视差滚动?

视差滚动是指多层背景以不同的速度移动，形成立体的运动效果，带来非常出色的视觉体验。

### 24. 怎么让 Chrome 支持小于 12px 的文字？

- 使用 css3 的 transform 缩放属性:`-webkit-transform:scale(0.5);`
- 使用图片：如果是内容固定不变情况下，使用将小于 12px 文字内容切出做图片，这样不影响兼容也不影响美观。

### 25. font-style 属性中 italic 和 oblique 的区别？

italic 和 oblique 这两个关键字都表示“斜体”的意思。

它们的区别在于，italic 是使用当前字体的斜体字体，而 oblique 只是单纯地让文字倾斜。如果当前字体没有对应的斜体字体，则退而求其次，解析 oblique，也就是单纯形状倾斜。

### 26. 设备像素、css 像素、设备独立像素、dpr、ppi 之间的区别？

设备像素指的是物理像素，一般手机的分辨率指的就是设备像素，一个设备的设备像素是不可变的。

css 像素和设备独立像素是等价的，不管在何种分辨率的设备上，css 像素的大小应该是一致的，css 像素是一个相对单位，它是相对于设备像素的，一个 css 像素的大小取决于页面缩放程度和 dpr 的大小。

dpr 指的是设备像素和设备独立像素的比值，一般的 pc 屏幕，dpr=1。在 iphone4 时，苹果推出了 retina 屏幕，它的 dpr 为 2。屏幕的缩放会改变 dpr 的值。

ppi 指的是每英寸的物理像素的密度，ppi 越大，屏幕的分辨率越大。

### 27. layoutviewport、visualviewport 和 idealviewport 的区别？

第一个视口是布局视口，在移动端显示网页时，由于移动端的屏幕尺寸比较小，如果网页使用移动端的屏幕尺寸进行布局的话，那么整个页面的布局都会显示错乱。所以移动端浏览器提供了一个 layoutviewport 布局视口的概念，使用这个视口来对页面进行布局展示，一般 layoutviewport 的大小为 980px，因此页面布局不会有太大的变化，我们可以通过拖动和缩放来查看到这个页面。

第二个视口指的是视觉视口，visualviewport 指的是移动设备上我们可见的区域的视口大小，一般为屏幕的分辨率的大小。visualviewport 和 layoutviewport 的关系，就像是我们通过窗户看外面的风景，视觉视口就是窗户，而外面的风景就是布局视口中的网页内容。

第三个视口是理想视口，由于 layoutviewport 一般比 visualviewport 要大，所以想要看到整个页面必须通过拖动和缩放才能实现。所以又提出了 idealviewport 的概念，idealviewport 下用户不用缩放和滚动条就能够查看到整个页面，并且页面在不同分辨率下显示的内容大小相同。idealviewport 其实就是通过修改 layoutviewport 的大小，让它等于设备的宽度，这个宽度可以理解为是设备独立像素，因此根据 idealviewport 设计的页面，在不同分辨率的屏幕下，显示应该相同。

### 28. `position:fixed`在 Android 下无效怎么处理？

因为移动端浏览器默认的 viewport 叫做 layoutviewport。在移动端显示时，因为 layoutviewport 的宽度大于移动端屏幕的宽度，所以页面会出现滚动条左右移动，fixed 的元素是相对 layoutviewport 来固定位置的，而不是移动端屏幕来固定位置的，所以会出现感觉 fixed 无效的情况。

如果想实现 fixed 相对于屏幕的固定效果，我们需要改变的是 viewport 的大小为 idealviewport，可以如下设置：

```html
<meta
  name="viewport"
  content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no"
/>
```

### 29. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？

多数显示器默认频率是 60Hz，即 1 秒刷新 60 次，所以理论上最小间隔为 1/60\*1000ms ＝ 16.7ms

### 30. png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过 webp？&#128128;

有七种常见的图片的格式。

- 第一种是 BMP 格式，它是无损压缩的，支持索引色和直接色的点阵图。由于它基本上没有进行压缩，因此它的文件体积一般比较大。

- 第二种是 GIF 格式，它是无损压缩的使用索引色的点阵图。由于使用了 LZW 压缩方法，因此文件的体积很小。并且 GIF 还支持动画和透明度。但因为它使用的是索引色，所以它适用于一些对颜色要求不高且需要文件体积小的场景。

- 第三种是 JPEG 格式，它是有损压缩的使用直接色的点阵图。由于使用了直接色，色彩较为丰富，一般适用于来存储照片。但由于使用的是直接色，可能文件的体积相对于 GIF 格式来说更大。

- 第四种是 PNG-8 格式，它是无损压缩的使用索引色的点阵图。它是 GIF 的一种很好的替代格式，它也支持透明度的调整，并且文件的体积相对于 GIF 格式更小。一般来说如果不是需要动画的情况，我们都可以使用 PNG-8 格式代替 GIF 格式。

- 第五种是 PNG-24 格式，它是无损压缩的使用直接色的点阵图。PNG-24 的优点是它使用了压缩算法，所以它的体积比 BMP 格式的文件要小得多，但是相对于其他的几种格式，还是要大一些。

- 第六种格式是 svg 格式，它是矢量图，它记录的图片的绘制方式，因此对矢量图进行放大和缩小不会产生锯齿和失真。它一般适合于用来制作一些网站 logo 或者图标之类的图片。

- 第七种格式是 webp 格式，它是支持有损和无损两种压缩方式的使用直接色的点阵图。使用 webp 格式的最大的优点是，在相同质量的文件下，它拥有更小的文件体积。因此它非常适合于网络图片的传输，因为图片体积的减少，意味着请求时间的减小，这样会提高用户的体验。这是谷歌开发的一种新的图片格式，目前在兼容性上还不是太好。

### 31. 什么是 CSS 预处理器/后处理器？

CSS 预处理器用一种专门的编程语言，为 CSS 增加了一些编程的特性，进行 Web 页面样式设计，然后再编译成正常的 CSS 文件。预处理器有 LESS、Sass、Stylus 等。

CSS 后处理器是对 CSS 进行处理，并最终生成 CSS 的预处理器，它属于广义上的 CSS 预处理器。例如：PostCSS，通常被视为在完成的样式表中根据 CSS 规范处理 CSS，让其更有效；目前最常做的是给 CSS 属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。

### 32. 阐述一下 CSSSprites

将一个页面涉及到的所有图片都包含到一张大图中去，然后利用 CSS 进行背景定位。

优点：减少 HTTP 请求数，极大地提高页面加载速度；增加图片信息重复度，提高压缩比，减少图片大小；更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现。

缺点：图片合并麻烦；维护麻烦，修改一个图片可能需要重新布局整个图片。

### 33. transition 和 animation 的区别

transition 关注的是 CSSproperty 的变化，property 值和时间的关系是一个三次贝塞尔曲线。

animation 作用于元素本身而不是样式属性，可以使用关键帧的概念，应该说可以实现更自由的动画效果。

### 34. min-width/max-width 和 min-height/max-height 属性间的覆盖规则？

- max-width 会覆盖 width，即使 width 是行类样式或者设置了 !important。

- min-width 会覆盖 max-width，此规则发生在 min-width 和 max-width 冲突的时候。

### 35. 什么是替换元素？

通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”。因此，`<img>`、`<video>`、`<iframe>`或者表单元素`<textarea>`和`<input>`都是典型的替换元素。

替换元素除了内容可替换这一特性以外，还有以下一些特性。

- 内容的外观不受页面上的 CSS 的影响。如何更改替换元素本身的外观需要类似 appearance 属性，或者浏览器自身暴露的一些样式接口。

- **有自己的尺寸**。在 Web 中，很多替换元素在没有明确尺寸设定的情况下，其默认的尺寸（不包括边框）是 300px×150px，如`<video>`、`<iframe>`或者`<canvas>`等，也有少部分替换元素为 0 像素，如`<img>`图片，而表单元素的替换元素的尺寸则和浏览器有关，没有明显的规律。

- 在很多 CSS 属性上有自己的一套表现规则。比较具有代表性的就是 vertical-align 属性，对于替换元素和非替换元素，vertical-align 属性值的解释是不一样的。vertical-align 的默认值的 baseline，被定义为字符 x 的下边缘，而替换元素的基线却被硬生生定义成了元素的下边缘。

- **所有的替换元素都是内联水平元素**，也就是替换元素和替换元素、替换元素和文字都是可以在一行显示的。但是，替换元素默认的 display 值却是不一样的，有的是 inline，有的是 inline-block。

### 36. `margin: auto` 的填充规则？

触发`margin: auto`的计算有一个前提条件，就是 width 或 height 为 auto 时，元素是具有对应方向的自动填充特性的。

- 如果一侧定值，一侧 auto，则 auto 为剩余空间大小。
- 如果两侧均是 auto，则平分剩余空间。

### 37. margin 无效的情形?

- display 为 inline 的非替换元素的竖直方向 margin 是无效的。对于内联替换元素，竖直方向 margin 有效，并且没有 margin 合并的问题。

（2）表格中的`<tr>`和`<td>`元素或者设置 display 为 table-cell 或 table-row 的元素的 margin 都是无效的。

（3）绝对定位元素非定位方位的 margin 值“无效”。

（4）定高容器的子元素的 margin-bottom 或者宽度定死的子元素的 margin-right 的定位“失效”。

### 38. line-height 的特殊性？

- 对于非替换元素的纯内联元素，其可视高度完全由 line-height 决定。
- 内联元素的高度由固定高度和不固定高度组成，这个不固定的部分就是行距。换句话说，line-height 之所以起作用，就是通过改变行距来实现的。
- 行距 = line-height - font-size。
- 对于纯文本元素，line-height 直接决定了最终的高度。但是，如果同时有替换元素，则 line-height 只能决定最小高度。
- 对于块级元素，line-height 对其本身是没有任何作用的，我们平时改变 line-height，块级元素的高度跟着变化实际上是通过改变块级元素里面内联级别元素占据的高度实现的。
- line-height 的默认值是 normal，还支持数值、百分比值以及长度值。为数值类型时，其最终的计算值是和当前 font-size 相乘后的值。为百分比值时，其最终的计算值是和当前 font-size 相乘后的值。为长度值时原意不变。
- 如果使用数值作为 line-height 的属性值，那么所有的子元素继承的都是这个值；但是，如果使用百分比值或者长度值作为属性值，那么所有的子元素继承的是最终的计算值。
- 无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的那个 line-height 决定的。

### 39. overflow 的特殊性？

- 一个设置了`overflow: hidden`声明的元素，假设同时存在 border 属性和 padding 属性，则当子元素内容超出容器宽度高度限制的时候，剪裁的边界是 borderbox 的内边缘，而非 paddingbox 的内边缘。
- HTML 中有两个标签是默认可以产生滚动条的，一个是根元素`<html>`，另一个是文本域`<textarea>`。
- 滚动条会占用容器的可用宽度或高度。
- 元素设置了`overflow: hidden`声明，里面内容高度溢出的时候，滚动依然存在，仅仅滚动条不存在！

### 40. 什么是层叠上下文？&#10084;

层叠上下文是 HTML 元素的三维概念，这些 HTML 元素在一条假想的相对于面向网页的用户的 z 轴上延伸，HTML 元素依据其自身属性按照优先级顺序占用层叠上下文的空间。

![层叠顺序](https://cavszhouyou-1254093697.cos.ap-chongqing.myqcloud.com/note-15.png)

### 41. 如何实现单行/多行文本溢出的省略？

```css
/*单行文本溢出,记住这三行*/
p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/*多行文本溢出*/
p {
  position: relative;
  line-height: 1.5em;
  height: 3em; /*显示两行*/
  overflow: hidden;
}

p:after {
  content: "...";
  position: absolute;
  bottom: 0;
  right: 0;
  background-color: #fff;
}
```

### 42. 常见的元素隐藏方式？

- 使用`display: none`隐藏元素，渲染树不会包含该渲染对象，因此该元素不会在页面中占据位置，也不会响应绑定的监听事件。
- 使用`visibility: hidden`隐藏元素。元素在页面中仍占据空间，但是不会响应绑定的监听事件。
- 使用`opacity: 0`将元素的透明度设置为 0，以此来实现元素的隐藏。元素在页面中仍然占据空间，并且能够响应元素绑定的监听事件。
- 通过使用绝对定位将元素移除可视区域内，以此来实现元素的隐藏。
- 通过 z-index 负值，来使其他元素遮盖住该元素，以此来实现隐藏。
- 通过 clip/clip-path 元素裁剪的方法来实现元素的隐藏，这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。
- 通过 transform:scale(0,0)来将元素缩放为 0，以此来实现元素的隐藏。这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

### 43. 主流浏览器内核私有属性 css 前缀？

- mozilla 内核 （firefox,flock 等） -moz
- webkit 内核 （safari,chrome 等） -webkit
- opera 内核 （opera 浏览器） -o
- trident 内核 （ie 浏览器） -ms

### 44. css reset 和 normalize.css 有什么区别？

css reset 是最早的一种解决浏览器间样式不兼容问题的方案，它的基本思想是将浏览器的所有样式都重置掉，从而达到所有浏览器样式保持一致的效果。但是使用这种方法，可能会带来一些性能上的问题，并且对于一些元素的不必要的样式的重置，其实反而会造成画蛇添足的效果。

后面出现一种更好的解决浏览器间样式不兼容的方法，就是 normalize.css ，它的思想是尽量的保留浏览器自带的样式，通过在原有的样式的基础上进行调整，来保持各个浏览器间的样式表现一致。相对与 css reset，normalize.css 的方法保留了有价值的默认值，并且修复了一些浏览器的 bug，而且使 normalize.css 不会造成元素复杂的继承链。

### 45. offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别？

clientWidth/clientHeight 返回的是元素的内部宽度，它的值只包含 content + padding，如果有滚动条，不包含滚动条。

offsetWidth/offsetHeight 返回的是元素的布局宽度，它的值包含 content + padding + border 包含了滚动条。

scrollWidth/scrollHeight 返回值包含 content + padding + 溢出内容的尺寸。
