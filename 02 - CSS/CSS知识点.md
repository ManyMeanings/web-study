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
