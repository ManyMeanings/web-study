- [1. 介绍一下 CSS 的盒子模型？&#10084;](#1-介绍一下-css-的盒子模型)
- [2. CSS 选择器有哪些？](#2-css-选择器有哪些)
- [3. CSS 中哪些属性可以继承？](#3-css-中哪些属性可以继承)
- [4. CSS 优先级算法如何计算？&#10084;](#4-css-优先级算法如何计算)
- [5. 关于 a 标签伪类“LVHA”的理解?](#5-关于-a-标签伪类lvha的理解)
- [6. 如何居中 div?&#10084;](#6-如何居中-div)
- [7. display 有哪些常用的值？。](#7-display-有哪些常用的值)
- [8. position 的值 relative 和 absolute 定位原点是？&#10084;](#8-position-的值-relative-和-absolute-定位原点是)
- [9. CSS3 有哪些新特性？](#9-css3-有哪些新特性)
- [10. 请解释一下 Flexbox（弹性盒布局模型），以及适用场景？](#10-请解释一下-flexbox弹性盒布局模型以及适用场景)
- [11. 如何用纯 CSS 绘制一个三角形？](#11-如何用纯-css-绘制一个三角形)
- [12. 一个满屏品字布局如何设计？](#12-一个满屏品字布局如何设计)
- [13. `li`与`li`之间有看不见的空白间隔是什么原因引起的？有什么解决办法？](#13-li与li之间有看不见的空白间隔是什么原因引起的有什么解决办法)
- [14. `width: auto`和`width: 100%`的区别?](#14-width-auto和width-100的区别)
- [15. 使用图片 base64 编码的优点和缺点是什么？](#15-使用图片-base64-编码的优点和缺点是什么)
- [16. margin 竖直方向上的重叠会产生什么问题？如何解决？&#10084;](#16-margin-竖直方向上的重叠会产生什么问题如何解决)
- [17. BFC 规范（块级格式化上下文）是什么？&#10084;](#17-bfc-规范块级格式化上下文是什么)
- [18. CSS 优化、提高性能的方法有哪些？&#10084;](#18-css-优化提高性能的方法有哪些)
- [19. 什么是响应式设计？响应式设计的基本原理是什么？](#19-什么是响应式设计响应式设计的基本原理是什么)
- [20. 怎么让 Chrome 支持小于 12px 的文字？](#20-怎么让-chrome-支持小于-12px-的文字)
- [21. font-style 属性中 italic 和 oblique 的区别？](#21-font-style-属性中-italic-和-oblique-的区别)
- [22. layoutviewport、visualviewport 和 idealviewport 的区别？](#22-layoutviewportvisualviewport-和-idealviewport-的区别)
- [23. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？](#23-如果需要手动写动画你认为最小时间间隔是多久为什么)
- [24. 介绍一下你了解的图片格式？&#128128;](#24-介绍一下你了解的图片格式)
- [25. 什么是 CSS 预处理器/后处理器？](#25-什么是-css-预处理器后处理器)
- [26. 什么是 CSSSprites？](#26-什么是-csssprites)
- [27. min-width/max-width 和 min-height/max-height 属性间的覆盖规则？](#27-min-widthmax-width-和-min-heightmax-height-属性间的覆盖规则)
- [28. 什么是替换元素？](#28-什么是替换元素)
- [29. line-height 特点？](#29-line-height-特点)
- [30. 什么是层叠上下文？&#10084;](#30-什么是层叠上下文)
- [31. 如何实现单行文本溢出的省略？](#31-如何实现单行文本溢出的省略)
- [32. 常见的元素隐藏方式？](#32-常见的元素隐藏方式)
- [33. 主流浏览器内核私有属性 css 前缀？](#33-主流浏览器内核私有属性-css-前缀)
- [34. css reset 和 normalize.css 有什么区别？](#34-css-reset-和-normalizecss-有什么区别)
- [35. offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别？](#35-offsetwidthoffsetheightclientwidthclientheight-与-scrollwidthscrollheight-的区别)
- [36. 浮动元素的特点？&#10084;](#36-浮动元素的特点)
- [37. 如何清除浮动？&#10084;](#37-如何清除浮动)
- [38. 标准文档流的特性？](#38-标准文档流的特性)
- [39. 三栏布局的实现](#39-三栏布局的实现)
- [40. 什么是包含块？](#40-什么是包含块)
- [41. 绝对定位元素与非绝对定位元素的百分比计算的区别](#41-绝对定位元素与非绝对定位元素的百分比计算的区别)
- [42. 不使用 border 画出 1px 高的线](#42-不使用-border-画出-1px-高的线)
- [43. css3 动画相关属性？](#43-css3-动画相关属性)
- [44. margin 变化的参考线？](#44-margin-变化的参考线)

### 1. 介绍一下 CSS 的盒子模型？&#10084;

CSS 盒子模型分为标准盒模型和 IE 盒模型，它们都由 content、padding、border 和 margin 组成。标准盒模型的 width 和 height 属性的范围只包含 content，而 IE 盒模型 width 和 height 属性的范围包含了 border、padding 和 content。

可以通过修改元素的 box-sizing 属性来改变元素的盒模型。

### 2. CSS 选择器有哪些？

-   id 选择器（#myid）
-   类选择器（.myclassname）
-   标签选择器（div）
-   后代选择器（h1 p）
-   交集选择器（p.myclassname）
-   并集选择器（h1, p）
-   相邻后代（子）选择器（ul>li）
-   兄弟选择器（li~a）
-   相邻兄弟选择器（li+a）
-   属性选择器（a[rel="external"]）
-   伪类选择器（a:hover）
-   伪元素选择器（::before）
-   通配符选择器（\*）

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

### 5. 关于 a 标签伪类“LVHA”的理解?

a 标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类 :link、:visited、:hover、:active

当链接未访问过时，当鼠标滑过 a 链接时，满足 :link 和 :hover 两种状态，要改变 a 标签的颜色，就必须将 :hover 伪类在 :link 伪类后面声明；当鼠标点击激活 a 链接时，同时满足 :link、:hover、:active 三种状态，要显示 a 标签激活时的样式，必须将 :active 声明放到 :link 和 :hover 之后，因此得出“LVHA”这个顺序。其他情况同理。

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

/*2. 利用绝对定位,未知容器的宽高，利用 transform 属性*/
div {
	position: absolute; /*相对定位或绝对定位均可*/
	width: 500px;
	height: 300px;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	background-color: red;
}

/*3. 利用flex布局*/
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

/*4. flex + margin: auto*/
.container {
	display: flex;
	min-height: 100vh;
	background: pink;
}
div {
	margin: auto;
	background: red;
}
```

### 7. display 有哪些常用的值？。

-   `block` 块类型，默认宽度为父元素宽度，可设置宽高，换行显示。
-   `inline` 行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
-   `inline-block` 默认宽度为内容宽度，可以设置宽高，同行显示。
-   `none` 元素不显示，并从文档流中移除。
-   `flex` 弹性盒子布局
-   `grid` 网格布局

### 8. position 的值 relative 和 absolute 定位原点是？&#10084;

relative 相对于其元素本身所在正常位置进行定位,设置偏移后仍然占用原来的文档空间。

absolute 定位原点是离自己最近的非 static 祖先元素（到 html 根标签为止）的左上角为原点，设置偏移后元素原先在正常文档流中所占的空间会关闭。

### 9. CSS3 有哪些新特性？

-   新增各种 CSS 选择器
-   边框圆角 （border-radius: 8px）
-   文本效果 （text-shadow text-decoration）
-   字体 （@font-face）
-   线性渐变 （gradient）
-   缩放，旋转，定位，倾斜，动画，多背景（transform）
-   过渡 （transition）
-   动画 （@keyframes）
-   多列布局 （multi-columnlayout）

### 10. 请解释一下 Flexbox（弹性盒布局模型），以及适用场景？

flex 布局是 CSS3 新增的一种布局方式，我们可以通过将一个元素的 display 属性值设置为 flex 从而使它成为一个 flex 容器，它的所有子元素都会成为它的项目。

一个容器默认有两条轴，一个是水平的主轴，一个是与主轴垂直的交叉轴。我们可以使用 flex-direction 来指定主轴的方向，使用 justify-content 来指定元素在主轴上的排列方式，使用 align-items 来指定元素在交叉轴上的排列方式，使用 flex-wrap 来规定换行方式。

对于容器中的项目，我们可以使用 order 属性来指定项目的排列顺序，使用 flex-grow 来指定当排列空间有剩余的时候，项目的放大比例，使用 flex-shrink 来指定当排列空间不足时，项目的缩小比例。align-self 属性允许单个项目有与其他项目不一样的对齐方式。

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

### 15. 使用图片 base64 编码的优点和缺点是什么？

base64 编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的 url 属性。

优点：少一个图片的 HTTP 请求。

缺点：编码后的大小会比原文件大小大 1/3；无法直接缓存；兼容性的问题（ie8+）

### 16. margin 竖直方向上的重叠会产生什么问题？如何解决？&#10084;

margin 重叠指的是标准文档流中，竖直方向的 margin 不叠加，只取较大的值作为 margin 。

一般来说可以分为四种情形：

第一种是相邻兄弟元素的 marin-bottom 和 margin-top 的值发生重叠。这种情况下可以通过设置其中一个元素为 BFC 来解决。

第二种是父元素的 margin-top 和子元素的 margin-top 发生重叠。可以为父元素设置 padding-top 值来分隔它们，也可以将父元素设置为 BFC。

第三种是高度为 auto 的父元素的 margin-bottom 和子元素的 margin-bottom 发生重叠。可以为父元素设置 padding-bottom 来分隔它们，可以为父元素设置一个高度，也可以将父元素设置为 BFC。

第四种情况，是没有内容的元素，自身的 margin-top 和 margin-bottom 发生的重叠。可以为其设置 border、padding 或者高度。

### 17. BFC 规范（块级格式化上下文）是什么？&#10084;

BFC 指的是块级格式化上下文，一个元素形成了 BFC 之后，那么它内部元素产生的布局不会影响到外部元素，外部元素的布局也不会影响到 BFC 中的内部元素。

特点：

-   BFC 内部的子元素，竖直方向 margin 会重叠。
-   BFC 在页面中是独立的容器，外面的元素不会影响里面的元素，反之亦然。
-   BFC 区域不与旁边的浮动区域区域重叠。（可以用来清除浮动带来的影响）。
-   在计算 BFC 的高度时，浮动子元素的高度的也会参与计算。

BFC 元素：

-   overflow: hidden 或 auto。
-   浮动元素 float ＝ left|right 或 inherit（≠none）
-   绝对定位元素 position ＝ absolute 或 fixed
-   非块级盒子的块级容器 display ＝ inline-block|flex|inline-flex|table-cell 或 table-caption

开发中的应用：

-   阻止 margin 重叠。
-   清除内部元素的浮动影响。
-   阻止元素被浮动元素覆盖。

### 18. CSS 优化、提高性能的方法有哪些？&#10084;

加载性能：

-   css 压缩：将写好的 css 进行打包压缩，可以减少很多的体积。
-   减少使用 @import,而建议使用 link。

选择器性能：

-   过滤掉无关的规则，这样样式系统就不会浪费时间去匹配它们了。
-   避免使用通配规则，只对需要用到的元素进行选择。
-   尽量少的去对标签进行选择，而是用 class。
-   尽量少的去使用后代选择器。后代选择器的开销是最高的，尽量将选择器的深度降到最低，最高不要超过三层。

渲染性能：

-   慎重使用高性能属性：浮动、定位。
-   尽量减少页面重排、重绘。
-   css 雪碧图。
-   不滥用 web 字体。（webfonts 通常体积庞大，而且一些浏览器在下载 webfonts 时会阻塞页面渲染损伤性能）

可维护性：

-   将具有相同属性的样式抽离出来，整合并通过 class 在页面中进行使用，提高 css 的可维护性。
-   样式与内容分离：将 css 代码定义到外部 css 中。

### 19. 什么是响应式设计？响应式设计的基本原理是什么？

响应式网站设计是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。基本原理是通过媒体查询检测不同的设备屏幕尺寸做处理。页面头部必须有 meta 声明的 viewport。

### 20. 怎么让 Chrome 支持小于 12px 的文字？

-   使用 css3 的 transform 缩放属性:`-webkit-transform:scale(0.5);`
-   使用图片：如果是内容固定不变情况下，使用将小于 12px 文字内容切出做图片，这样不影响兼容也不影响美观。

### 21. font-style 属性中 italic 和 oblique 的区别？

italic 和 oblique 这两个关键字都表示“斜体”的意思。

它们的区别在于，italic 是使用当前字体的斜体字体，而 oblique 只是单纯地让文字倾斜。如果当前字体没有对应的斜体字体，则退而求其次，解析 oblique，也就是单纯形状倾斜。

### 22. layoutviewport、visualviewport 和 idealviewport 的区别？

layoutviewport 是布局视口。在移动端显示网页时，由于移动端的屏幕尺寸比较小，如果网页使用移动端的屏幕尺寸进行布局的话，那么整个页面的布局都会显示错乱。一般 layoutviewport 的大小为 980px，因此页面布局不会有太大的变化，可以通过拖动和缩放来查看到这个页面。

visualviewport 指的是视觉视口。visualviewport 指的是移动设备上我们可见的区域的视口大小，一般为屏幕的分辨率的大小。

idealviewport 是理想视口。用户不用缩放和滚动条就能够查看到整个页面，并且页面在不同分辨率下显示的内容大小相同。idealviewport 其实就是通过修改 layoutviewport 的大小，让它等于设备的宽度，因此根据 idealviewport 设计的页面，在不同分辨率的屏幕下，显示应该相同。

### 23. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？

多数显示器默认频率是 60Hz，即 1 秒刷新 60 次，所以理论上最小间隔为 1/60\*1000ms ＝ 16.7ms

### 24. 介绍一下你了解的图片格式？&#128128;

有七种常见的图片的格式。

-   BMP：无损压缩，支持索引色和直接色的点阵图。由于它基本上没有进行压缩，因此它的文件体积一般比较大。

-   GIF：无损压缩，使用索引色的点阵图，支持动画和透明度。由于使用了 LZW 压缩方法，因此文件的体积很小。但因为它使用的是索引色，所以它适用于一些对颜色要求不高且需要文件体积小的场景。

-   JPEG：有损压缩，使用直接色的点阵图。由于使用了直接色，色彩较为丰富，一般适用于来存储照片。但由于使用的是直接色，可能文件的体积相对于 GIF 格式来说更大。

-   PNG-8：无损压缩，使用索引色的点阵图。它是 GIF 的一种很好的替代格式，它也支持透明度的调整，并且文件的体积相对于 GIF 格式更小。一般来说如果不是需要动画的情况，我们都可以使用 PNG-8 格式代替 GIF 格式。

-   PNG-24：无损压缩，使用直接色的点阵图。PNG-24 的优点是它使用了压缩算法，所以它的体积比 BMP 格式的文件要小得多，但是相对于其他的几种格式，还是要大一些。

-   svg：矢量图，记录的图片的绘制方式，因此对矢量图进行放大和缩小不会产生锯齿和失真。它一般适合于用来制作一些网站 logo 或者图标之类的图片。

-   webp：支持有损和无损两种压缩方式，使用直接色的点阵图。在相同质量的文件下，它拥有更小的文件体积。这是谷歌开发的一种新的图片格式，目前在兼容性上还不是太好。

### 25. 什么是 CSS 预处理器/后处理器？

CSS 预处理器用一种专门的编程语言，为 CSS 增加了一些编程的特性，进行 Web 页面样式设计，然后再编译成正常的 CSS 文件。预处理器有 LESS、Sass、Stylus 等。

CSS 后处理器是对 CSS 进行处理，并最终生成 CSS 的预处理器，它属于广义上的 CSS 预处理器。例如：PostCSS，通常被视为在完成的样式表中根据 CSS 规范处理 CSS，让其更有效；目前最常做的是给 CSS 属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。

### 26. 什么是 CSSSprites？

将一个页面涉及到的所有图片都包含到一张大图中去，然后利用 CSS 进行背景定位。

优点：减少 HTTP 请求数，极大地提高页面加载速度；增加图片信息重复度，提高压缩比，减少图片大小；更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现。

缺点：图片合并麻烦；维护麻烦，修改一个图片可能需要重新布局整个图片。

### 27. min-width/max-width 和 min-height/max-height 属性间的覆盖规则？

-   max-width 会覆盖 width，即使 width 是行类样式或者设置了 !important。

-   min-width 会覆盖 max-width，此规则发生在 min-width 和 max-width 冲突的时候。

### 28. 什么是替换元素？

通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”。因此，`<img>`、`<video>`、`<iframe>`或者表单元素`<textarea>`和`<input>`都是典型的替换元素。

替换元素除了内容可替换这一特性以外，还有以下一些特性。

-   内容的外观不受页面上的 CSS 的影响。如何更改替换元素本身的外观需要类似 appearance 属性，或者浏览器自身暴露的一些样式接口。

-   **有自己的尺寸**。在 Web 中，很多替换元素在没有明确尺寸设定的情况下，其默认的尺寸（不包括边框）是 300px×150px，如`<video>`、`<iframe>`或者`<canvas>`等，也有少部分替换元素为 0 像素，如`<img>`图片，而表单元素的替换元素的尺寸则和浏览器有关，没有明显的规律。

-   **所有的替换元素都是内联水平元素**，也就是替换元素和替换元素、替换元素和文字都是可以在一行显示的。但是，替换元素默认的 display 值却是不一样的，有的是 inline，有的是 inline-block。

### 29. line-height 特点？

-   对于非替换元素的纯内联元素，其可视高度完全由 line-height 决定。
-   内联元素的高度由固定高度和不固定高度组成，这个不固定的部分就是行距。line-height 之所以起作用，就是通过改变行距来实现的，行距 = line-height - font-size。
-   对于纯文本元素，line-height 直接决定了最终的高度。但是，如果同时有替换元素，则 line-height 只能决定最小高度。
-   对于块级元素，line-height 对其本身是没有任何作用的，我们平时改变 line-height，块级元素的高度跟着变化实际上是通过改变块级元素里面内联级别元素占据的高度实现的。
-   如果使用数值作为 line-height 的属性值，那么所有的子元素继承的都是这个值；但是，如果使用百分比值或者长度值作为属性值，那么所有的子元素继承的是最终的计算值。
-   无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的那个 line-height 决定的。

### 30. 什么是层叠上下文？&#10084;

层叠上下文是 HTML 元素的三维概念，这些 HTML 元素在一条假想的相对于面向网页的用户的 z 轴上延伸，HTML 元素依据其自身属性按照优先级顺序占用层叠上下文的空间。

![层叠顺序](https://cavszhouyou-1254093697.cos.ap-chongqing.myqcloud.com/note-15.png)

### 31. 如何实现单行文本溢出的省略？

```css
p {
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
}
```

### 32. 常见的元素隐藏方式？

-   使用`display: none`隐藏元素，渲染树不会包含该渲染对象，因此该元素不会在页面中占据位置，也不会响应绑定的监听事件。
-   使用`visibility: hidden`隐藏元素。元素在页面中仍占据空间，但是不会响应绑定的监听事件。
-   使用`opacity: 0`将元素的透明度设置为 0，以此来实现元素的隐藏。元素在页面中仍然占据空间，并且能够响应元素绑定的监听事件。
-   通过 z-index 负值，来使其他元素遮盖住该元素，以此来实现隐藏。
-   通过 transform:scale(0,0)来将元素缩放为 0，以此来实现元素的隐藏。这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

### 33. 主流浏览器内核私有属性 css 前缀？

-   mozilla 内核 （firefox,flock 等） -moz
-   webkit 内核 （safari,chrome 等） -webkit
-   opera 内核 （opera 浏览器） -o
-   trident 内核 （ie 浏览器） -ms

### 34. css reset 和 normalize.css 有什么区别？

css reset 是最早的一种解决浏览器间样式不兼容问题的方案，它的基本思想是将浏览器的所有样式都重置掉，从而达到所有浏览器样式保持一致的效果。但是使用这种方法，可能会带来一些性能上的问题，并且对于一些元素的不必要的样式的重置，其实反而会造成画蛇添足的效果。

后面出现一种更好的解决浏览器间样式不兼容的方法，就是 normalize.css ，它的思想是尽量的保留浏览器自带的样式，通过在原有的样式的基础上进行调整，来保持各个浏览器间的样式表现一致。相对与 css reset，normalize.css 的方法保留了有价值的默认值，并且修复了一些浏览器的 bug，而且使 normalize.css 不会造成元素复杂的继承链。

### 35. offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别？

clientWidth/clientHeight 返回的是元素的内部宽度，它的值只包含 content + padding，如果有滚动条，不包含滚动条。

offsetWidth/offsetHeight 返回的是元素的布局宽度，它的值包含 content + padding + border 包含了滚动条。

scrollWidth/scrollHeight 返回值包含 content + padding + 溢出内容的尺寸。

### 36. 浮动元素的特点？&#10084;

-   浮动元素脱离标准流。
-   浮动元素互相贴靠。
-   浮动元素有“字围”效果。
-   收缩：一个浮动的元素，如果没有设置 width，那么将自动收缩为内容的宽度。

### 37. 如何清除浮动？&#10084;

-   加高法：给浮动元素的父元素设置高度（大于浮动子元素的高度）。
-   隔墙法：用`<div style="clear: both"></div>`隔开两个浮动的元素。
-   内墙法：在浮动元的父元素里修一堵墙`<div style="clear: both"></div>`，使该元素被子元素撑出高度。
-   给浮动元素的父元素设置属性`overflow: hidden;`。
-   加一个 clearfix 类

```css
.clearfix:after {
	content: '.';
	display: block;
	height: 0;
	visibility: hidden;
	clear: both;
}
.clearfix {
	*zoom: 1; /* 解决ie6，ie7的兼容问题*/
}
```

### 38. 标准文档流的特性？

-   空白折叠：无论多少个空格、换行、tab，都会折叠成一个空格。
-   高矮不齐，底边对齐
-   自动换行

### 39. 三栏布局的实现

高度已知，左右宽度固定，中间自适应。

1. 流体布局：左侧设置左浮动，右侧设置右浮动，中间不浮动，设置左右边距为边栏的宽度，注意三个 div 的顺序为“左右中”
2. BFC 布局：方案与第一种类似，中间设置为 BFC，不需要设置左右边距
3. 绝对定位：左侧绝对定位`left: 0`，右侧也绝对定位`right: 0`，中间绝对定位，左右设置为宽度即可
4. flex 布局：左右设置宽度，中间`flex-grow: 1`
5. 圣杯布局：利用左浮动，负 margin 和相对定位，容器需设为 BFC 撑开高度（overflow: hidden）
6. 双飞翼布局：相比圣杯布局不使用定位，在 middle 的 div 里又插入一个 div，通过调整内部 div 的 margin 值，实现中间栏自适应
7. 网格布局：如下

```css
.left-center-right {
	display: grid;
	width: 100%;
	grid-template-rows: 100px;
	grid-template-columns: 300px auto 300px; /* 重要：设置网格为三列，并设置每列的宽度。即可。*/
}
```

### 40. 什么是包含块？

包含块就是元素用来计算和定位的一个框。

1. 根元素被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。
2. 对于其他元素，如果该元素的 position 是 relative 或者 static，则包含块由其最近的块容器祖先盒的 contentbox 边界形成。
3. 如果元素 position:fixed，则包含块是“初始包含块”。
4. 如果元素 position:absolute，则包含块由最近的 position 不为 static 的祖先元素建立。

### 41. 绝对定位元素与非绝对定位元素的百分比计算的区别

绝对定位元素的宽高百分比是相对于临近的 position 不为 static 的祖先元素的 paddingbox 来计算的。

非绝对定位元素的宽高百分比则是相对于父元素的 contentbox 来计算的。

### 42. 不使用 border 画出 1px 高的线

```css
<div style="height:1px;overflow:hidden;background:red"></div>
```

### 43. css3 动画相关属性？

-   依靠 CSS3 中提出的三个属性：transition、transform、animation
-   transition：定义了元素在变化过程中是怎么样的，包含 transition-property、transition-duration、transition-timing-function、transition-delay。
-   transform：定义元素的变化结果，包含 rotate、scale、skew、translate。
-   animation：动画定义了动作的每一帧（@keyframes）有什么效果，包括 animation-name，animation-duration、animation-timing-function、animation-delay、animation-iteration-count、animation-direction

### 44. margin 变化的参考线？

margin-top、margin-left 以 margin 外边缘为参考线；margin-bottom、margin-right 以 border 为参考线（正负值都是如此）。
