- [长度单位](#长度单位)
  - [绝对单位](#绝对单位)
  - [相对单位](#相对单位)
- [文本和字体样式](#文本和字体样式)
  - [基础样式](#基础样式)
  - [文本布局样式](#文本布局样式)
  - [列表属性](#列表属性)
- [背景属性](#背景属性)
- [选择器](#选择器)
  - [伪类](#伪类)
  - [伪元素](#伪元素)
  - [选择器优先级计算](#选择器优先级计算)
- [定位](#定位)
  - [相对定位](#相对定位)
  - [绝对定位](#绝对定位)
  - [固定定位](#固定定位)
  - [`z-index`](#z-index)
- [CSS3 动画](#css3-动画)
  - [过渡（transition）](#过渡transition)
  - [2D 转换](#2d-转换)
    - [缩放（scale）](#缩放scale)
    - [位移（translate）](#位移translate)
    - [旋转（rotate）](#旋转rotate)
  - [3D 转换](#3d-转换)
    - [旋转（rotateX rotateY rotateZ）](#旋转rotatex-rotatey-rotatez)
    - [移动（translateX translateY translateZ）](#移动translatex-translatey-translatez)
    - [透视](#透视)
    - [3D 呈现](#3d-呈现)
  - [动画](#动画)
    - [定义动画的步骤](#定义动画的步骤)
    - [动画属性](#动画属性)
- [flex 布局](#flex-布局)
  - [属性](#属性)

## 长度单位

### 绝对单位

- in：英寸 Inches
- cm：厘米 Centimeters
- mm：毫米 Millimeters
- pt：点 Points，或者叫英镑
- pc：皮卡 Picas

**换算关系：**

1 in = 2.54 cm = 25.4 mm = 72 pt = 6 pc

### 相对单位

- px：像素
- em：在 font-size 中使用是相对于父元素的字体大小，在其他属性中使用是相对于自身的字体大小，如 width
- rem：根元素的字体大小
- lh：元素的 line-height
- vw：视窗宽度的 1%
- vh：视窗高度的 1%

## 文本和字体样式

### 基础样式

- `font-size: 20px`：字体大小
- `font-family: Helvetica, Arial, sans-serif`：字体类型
- `font-style: normal/italic/oblique`：设置字体为斜体
- `font-weight: normal/bold`：字体的粗细
- `text-transform: none/uppercase/lowercase/capitalize`：大小写转换
- `text-decoration: none/underline/overline/line-through`：字体装饰
- `text-shadow: 4px 4px 5px red`：文字阴影，设置水平、垂直偏移，模糊半径，阴影颜色
- `color: red`：文本颜色

### 文本布局样式

- `text-align: left/right/center/justify`：文本左对齐/右对齐/居中/展开
- `line-height: 30px/1.5`：行高
- `letter-spacing: 2px`：字母间距
- `word-spacing: 4px`：单词间距
- `text-indent: 20px`：首行缩进

### 列表属性

- `list-style-type: none/disc/circle/square/...`：设置列表项前的图标
- `list-style-image: url(url)`：设置列表项前的图标为图片
- `list-style-position: outside/inside`：列表项内容换行顶不顶格

## 背景属性

- `background-color: red`：背景颜色
- `background-image: url(url)`：将图像设置为背景
- `background-repeat: no-repeat/repeat-x/repeat-y`：设置背景图像是否重复及如何重复，默认平铺满
- `background-position: 向右偏移量 向下偏移量`：设置背景图片在当前容器中的位置，可以用像素值或单词描述
- `background-attachment: scroll/fixed`：设置背景图片是否跟随滚动条滚动
- `background-size: cover/contain/50% 50%`：设置背景图片尺寸
- `background-origin：padding-box/border-box/content-box`：控制背景从什么地方开始显示
- `background-clip: content-box/border-box/padding-box`：设置元素的背景是否延伸到选定边框外面
- `background-image: linear-gradient(方向, 起始颜色, 终止颜色)/radial-gradient(辐射的半径大小, 中心的位置, 起始颜色, 终止颜色)`背景渐变

## 选择器

- id 选择器（#myid）
- 类选择器（.myclassname）
- 标签选择器（div）
- 后代选择器（h1 p）
- 交集选择器（p.myclassname）
- 并集选择器（h1, p）
- 相邻后代（子）选择器（ul>li）
- 兄弟选择器（li~a）
- 相邻兄弟选择器（li+a）
- 属性选择器（a[rel="external"]）
- 伪类选择器（a:hover）
- 伪元素选择器（::before）
- 通配符选择器（\*）

### 伪类

- `:link`,`:visited`,`:hover`,`:activate`：超链接的四个状态
- `:focus`：选择获取焦点的输入字段
- `:not(.first-item)`：选中除了第一个项的其他项
- `:first-child`,`last-child`：选中匹配元素的第一个/最后一个子元素
- `:nth-child(an+b)`：匹配第 an+b(n=0,1,2,3,...) 个子元素
- `:only-child`：匹配元素是其父元素中只有唯一一个子元素
- `:checked`：匹配被选中单选/多选按钮
- `:disabled`：匹配禁用的表单元素
- `:valid`,`:invalid`：匹配条件验证正确/不正确的表单元素
- `:read-write`：匹配处于编辑状态的元素

### 伪元素

- `::before`,`::after`：在被选元素前/后插入内容，用`content: "content"`指定
- `::first-line`：匹配元素中第一行的文本
- `::first-letter`：匹配元素的首字母

### 选择器优先级计算

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

## 定位

### 相对定位

不脱标，老家留坑，别人不会把它的位置挤走。

**作用：**

- 微调元素
- 做绝对定位的参考

### 绝对定位

绝对定位脱标，标签就不区分所谓的行内元素、块级元素了

**参考点：**

- 如果用 top 描述，那么参考点就是页面的左上角，而不是浏览器的左上角
- 如果用 bottom 描述，那么参考点就是浏览器**首屏**窗口尺寸，对应的页面的左下角
- 一个绝对定位的元素，如果父辈元素中也出现了已定位（无论是绝对定位、相对定位，还是固定定位）的元素，那么将以父辈这个元素，为参考点

### 固定定位

就是相对浏览器窗口进行定位。无论页面如何滚动，这个盒子显示的位置不变。

**作用：**

- 网页右下角的“返回到顶部”
- 顶部导航条

### `z-index`

表示谁压着谁。数值大的压盖住数值小的。

**特性：**

- 属性值大的位于上层，属性值小的位于下层。
- z-index 值没有单位，就是一个正整数。默认的 z-index 值是 0。
- 如果大家都没有 z-index 值，或者 z-index 值一样，那么在 HTML 代码里写在后面，谁就在上面能压住别人。定位了的元素，永远能够压住没有定位的元素。
- 只有定位了的元素，才能有 z-index 值。也就是说，不管相对定位、绝对定位、固定定位，都可以使用 z-index 值。而浮动的元素不能用。
- 从父现象：父亲怂了，儿子再牛逼也没用。意思是，如果父亲 1 比父亲 2 大，那么，即使儿子 1 比儿子 2 小，儿子 1 也能在最上层。

## CSS3 动画

### 过渡（transition）

transition 的中文含义是过渡。过渡是 CSS3 中具有颠覆性的一个特征，可以实现元素不同状态间的平滑过渡（补间动画），经常用来制作动画效果。

- `transition-property: all`：希望过渡的属性
- `transition-duration: 1s`：过渡的持续时间
- `transition-timing-function: linear/ease/ease-in/ease-out/ease-in-out`：线性/减速/加速/减速/先加速后减速
- `transition-delay: 1s`：过渡延迟

综合写法：`transition: 让哪些属性进行过度 过渡的持续时间 运动曲线 延迟时间`

### 2D 转换

#### 缩放（scale）

`transform: scale(x, y)`：x 代表水平方向缩放倍数，y 代表垂直方向缩放倍数。

#### 位移（translate）

`transform: translate(x, y)`：参数为百分比，相对于自身移动。正值：向右和向下。 负值：向左和向上。如果只写一个值，则表示水平移动。

#### 旋转（rotate）

- `transform: rotate(45deg)`：正值顺时针，负值逆时针。
- `transform-origin: center bottom`：改变旋转的坐标原点

### 3D 转换

#### 旋转（rotateX rotateY rotateZ）

伸出左手，让拇指和食指成“L”形，大拇指向右，食指向上，中指指向前方。拇指、食指和中指分别代表 X、Y、Z 轴的正方向，这样我们就建立了一个左手坐标系。浏览器的这个平面，是 X 轴、Y 轴；垂直于浏览器的平面，是 Z 轴。

左手握住旋转轴，竖起拇指指向旋转轴的正方向，正向就是其余手指卷曲的方向。所有的 3d 旋转，对着正方向去看，都是顺时针旋转。

- `transform: rotateX(360deg)`：绕 x 轴旋转 360 度
- `transform: rotateY(360deg)`：绕 y 轴旋转 360 度
- `transform: rotateZ(360deg)`：绕 z 轴旋转 360 度

#### 移动（translateX translateY translateZ）

- `transform: translateX(100px)`
- `transform: translateY(100px)`：
- `transform: translateZ(100px)`：

#### 透视

透视可以将一个 2D 平面，在转换的过程当中，呈现 3D 效果。但仅仅只是视觉呈现出 3D 效果，并不是真正的 3D。

`perspective: 500px`; 设置的是用户的眼睛距离，平面的距离

**用法：**

- 作为一个属性，设置给父元素，作用于所有 3D 转换的子元素
- 作为 transform 属性的一个值，作用于元素自身

#### 3D 呈现

3D 元素构建是指某个图形是由多个元素构成的，可以给这些元素的父元素设置`transform-style: preserve-3d`来使其变成一个真正的 3D 图形。

### 动画

#### 定义动画的步骤

1. 通过`@keyframes`定义动画
2. 将这段动画通过百分比，分割成多个节点，在各节点中分别定义各自属性
3. 在指定元素里，通过`animation`属性调用动画

**伪代码：**

```css
定义动画：
      @keyframes 动画名{
          from{ 初始状态 }
          to{ 结束状态 }
      }

  调用：
      animation: 动画名称 持续时间；
```

#### 动画属性

`animation: 定义的动画名称 持续时间 执行次数 是否反向 运动曲线 延迟执行`

## flex 布局

**优势：**

- flex 布局的子元素不会脱离文档流，很好地遵从了“流的特性”。
- flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范。

### 属性

**flex 容器：**

- `flex-direction: row/column/row-reverse/column-reverse`
- `flex-wrap: wrap/nowrap`
- `justify-content: flex-start/flex-end/center/space-around/space-between`
- `align-items: flex-start/flex-end/center/stretch`

**flex 元素：**

- `order: 1`
- `align-self: flex-start/flex-end/center/stretch`
- `flex-grow: 1`
- `flex-shrink: 1`
- `flex-basis: auto`
