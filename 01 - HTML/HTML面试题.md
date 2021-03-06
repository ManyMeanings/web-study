- [1. DOCTYPE 的作用是什么？&#10084;](#1-doctype-的作用是什么)
- [2. 标准模式与兼容模式有什么区别？](#2-标准模式与兼容模式有什么区别)
- [3. SGML, HTML, XML 和 XHTML 的区别？](#3-sgml-html-xml-和-xhtml-的区别)
- [4. 行内元素与块级元素的区别？&#10084;](#4-行内元素与块级元素的区别)
- [5. 页面导入样式时，使用 link 和 @import 有什么区别？](#5-页面导入样式时使用-link-和-import-有什么区别)
- [6. HTML5 有哪些新特性，移除了那些元素？&#128128;](#6-html5-有哪些新特性移除了那些元素)
- [7. 你对 HTML 语义化的理解？](#7-你对-html-语义化的理解)
- [8. 前端需要注意哪些 SEO？&#128128;](#8-前端需要注意哪些-seo)
- [9. HTML5 的离线储存怎么使用？&#10084;](#9-html5-的离线储存怎么使用)
- [10. cookies，sessionStorage 和 localStorage 的区别是什么？&#10084;](#10-cookiessessionstorage-和-localstorage-的区别是什么)
- [11. iframe 有哪些缺点？](#11-iframe-有哪些缺点)
- [12. label 的作用是什么？如何使用？](#12-label-的作用是什么如何使用)
- [13. HTML5 的 form 的自动完成功能是什么？](#13-html5-的-form-的自动完成功能是什么)
- [14. `<img>`的`title`和`alt`属性有什么区别？](#14-img的title和alt属性有什么区别)
- [15. 渐进增强和优雅降级的定义](#15-渐进增强和优雅降级的定义)
- [16. `<input>`标签中 disabled 和 readonly 的区别？](#16-input标签中-disabled-和-readonly-的区别)
- [17. viewport 相关属性？](#17-viewport-相关属性)

### 1. DOCTYPE 的作用是什么？&#10084;

DOCTYPE 用来声明 DTD 规范。一个主要用途是文件的合法性验证，如果文件代码不合法，那么浏览器解析时便会出错。

HTML5 的写法是`<!DOCTYPE html>`。

> DTD（Document Type Definition）：文档类型定义，是一系列的语法规则。告诉浏览器，我是什么文档类型，你要用什么协议来解析我。

### 2. 标准模式与兼容模式有什么区别？

标准模式的渲染方式和 JS 引擎的解析方式都是以该浏览器支持的最高标准运行。

兼容模式中页面以宽松的向后兼容的方式显示，模拟老式浏览器的行为以防止站点无法工作。

### 3. SGML, HTML, XML 和 XHTML 的区别？

SGML 是标准通用标记语言，是一种定义电子文档结构和描述其内容的国际标准语言，是所有电子文档标记语言的起源。

HTML 是超文本标记语言，主要是用于规定怎么显示网页。

XML 是可拓展标记语言，是未来网页语言的发展方向，XML 和 HTML 的最大区别在于 XML 的标签可以自己创建，数量无限多。

XHTML 和 HTML 没有本质的区别，但是相比 HTML 更严格，例如标签必须小写，标签必须有闭合标签等。

### 4. 行内元素与块级元素的区别？&#10084;

-   **格式上**，行内元素不会以新行开始，块级元素会新起一行。
-   **内容上**，行内元素只能包含文本和其他行内元素，块级元素可以包含行内元素和其他块级元素。
-   **样式上**，行内元素设置`width`和`height`无效，设置`margin`和`padding`的水平方向有效，竖直方向无效。

### 5. 页面导入样式时，使用 link 和 @import 有什么区别？

-   **从属关系**：link 是 HTML 的标签，不仅可以加载 CSS 文件，还可以定义 rel 连接属性，引入网站图标等；@import 是 CSS 提供的语法规则，只能导入样式表。
-   **加载顺序**：link 引入的 CSS 同时加载，@import 引入的 CSS 在页面加载完毕后加载。
-   **兼容性**： link 无兼容性问题，@import 只适用于 IE5+ 的浏览器。
-   **DOM**：可以用 JS 插入 link 标签改变样式，无法使用 @import 的方式。

### 6. HTML5 有哪些新特性，移除了那些元素？&#128128;

新增的有：

-   语义化标签： header，footer，nav，article，section
-   新表单类型：email，tel，date，range
-   新表单属性：placehoder，required
-   视频和音频：video，audio
-   绘图：canvas
-   矢量图形：svg
-   拖放：Drag， drop
-   地理定位
-   离线存储：manifest
-   Web 存储：localStorage，sessionStorage
-   WebSocket：全双工通讯
-   多任务：webworker
-   历史管理：history
-   页面可见性事件：visibilitychange
-   跨窗口通信：postMessage

移除的元素有：

-   纯表现的元素：basefont，big，center，font, s，strike，tt，u
-   对可用性产生负面影响的元素：frame，frameset，noframes

### 7. 你对 HTML 语义化的理解？

-   用正确的标签做正确的事情。
-   语义化让页面的内容结构更清晰，便于浏览器解析。
-   利于 SEO，搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重。
-   容易阅读和维护。

例子：从页面显示效果来看，被`<b>`和`<strong>`包围的文字将会被加粗，而被`<i>`和`<em>` 包围的文字将以斜体的形式呈现。但是`<b>`和`<i>`表示无意义的加粗，无意义的斜体，不如直接在 css 样式表设置。而`<em>`和`<strong>`是语义样式标签。`<em>`表示一般的强调文本，而`<strong>`表示比`<em>`语义更强的强调文本。使用阅读设备阅读网页时，`<strong>` 会重读。

### 8. 前端需要注意哪些 SEO？&#128128;

-   合理的 title、description、keywords：搜索对这三项的权重逐个减小，title 值强调重点即可，重要关键词出现不要超过 2 次，而且要靠前，不同页面 title 要有所不同；description 把页面内容高度概括，长度合适，不可过分堆砌关键词，不同页面 description 有所不同；keywords 列举出重要关键词即可。
-   语义化的 HTML 代码。
-   重要内容 HTML 代码放在最前：搜索引擎抓取 HTML 顺序是从上到下，有的搜索引擎对抓取长度有限制，保证重要内容肯定被抓取。
-   重要内容不要用 js 输出：爬虫不会执行 js 获取内容。
-   少用 iframe：搜索引擎不会抓取 iframe 中的内容。
-   非装饰性图片必须加 alt。
-   提高网站速度：网站速度是搜索引擎排序的一个重要指标。

### 9. HTML5 的离线储存怎么使用？&#10084;

简介：在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。

原理：HTML5 的离线存储是基于一个新建的 .appcache 文件的缓存机制（不是存储技术），通过这个文件上的解析清单离线存储资源。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

如何使用：

1. 创建一个和该 html 文件同名的 manifest 文件，并在 html 标签加入 manifest 属性：`<html lang="en" manifest="index.manifest">`
2. 在 index.manifest 文件中列出需要离线缓存的资源，格式如下：

```
CACHE MANIFEST

# 要缓存的文件
CACHE:
    images/img1.jpg
    images/img2.jpg

# 指定必须联网才能访问的文件
NETWORK:
    images/img3.jpg
    images/img4.jpg

# 当前页面无法访问是回退的页面或者访问不到某资源时替换的资源
FALLBACK:
    404.html
```

### 10. cookies，sessionStorage 和 localStorage 的区别是什么？&#10084;

cookie 其实最开始是服务器端用于记录用户状态的一种方式，由服务器设置，在客户端存储，然后每次发起同源请求时，发送给服务器端。cookie 最多能存储 **4k 数据**，它的**生存时间由 expires 属性指定**，并且 cookie 只能被**同域的页面**（不要求协议和端口相同）访问共享。

sessionStorage 是 html5 提供的一种浏览器本地存储的方法，它借鉴了服务器端 session 的概念，代表的是一次会话中所保存的数据。它一般能够存储 **5M 或者更大**的数据，它**在当前窗口关闭后就失效了**，并且 sessionStorage 只能被**同一个窗口的同源页面**所访问共享。

localStorage 也是 html5 提供的一种浏览器本地存储的方法，它一般也能够存储 **5M 或者更大的数据**。它和 sessionStorage 不同的是，**除非手动删除它，否则它不会失效**，并且 localStorage 也只能被**同源页面**所访问共享。

**cookies 的安全属性：**

-   value：如果用于保存用户登录态，应该将该值加密，不能使用明文的用户标识
-   http-only：不能通过 JS 访问 Cookie，减少 XSS 攻击
-   secure：只能在协议为 HTTPS 的请求中携带
-   same-site：规定浏览器不能在跨域请求中携带 Cookie，减少 CSRF 攻击

### 11. iframe 有哪些缺点？

-   iframe 会阻塞主页面的 onload 事件。window 的 onload 事件需要在所有 iframe 加载完毕后（包含里面的元素）才会触发。
-   搜索引擎的检索程序无法解读这种页面，不利于网页的 SEO。
-   iframe 和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
-   浏览器的后退按钮失效。
-   小型的移动设备无法完全显示框架。

### 12. label 的作用是什么？如何使用？

label 标签来定义表单标签间的控制关系，当用户选择该标签时，浏览器会自动将焦点转到和 label 标签相关的表单控件上。

```html
<label for="name"></label> <input type="text" name="name" id="name" />
```

### 13. HTML5 的 form 的自动完成功能是什么？

`autocomplete`属性规定输入字段是否应该启用自动完成功能。默认为启用，设置为 `autocomplete=off`可以关闭该功能。

自动完成允许浏览器预测对字段的输入。当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段中填写的选项。

### 14. `<img>`的`title`和`alt`属性有什么区别？

`title`通常当鼠标滑动到元素上的时候显示。

`alt`是`<img>`的特有属性，是图片内容的等价描述，用于图片无法加载时显示、读屏器阅读图片。可提图片高可访问性，除了纯装饰图片外都必须设置有意义的值，搜索引擎会重点分析。

### 15. 渐进增强和优雅降级的定义

渐进增强：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

优雅降级：一开始就根据高版本浏览器构建完整的功能，然后再针对低版本浏览器进行兼容。

### 16. `<input>`标签中 disabled 和 readonly 的区别？

disabled 指当 input 元素加载时禁用此元素。input 内容不会随着表单提交。

readonly 规定输入字段为只读。input 内容会随着表单提交。

无论设置 readonly 还是 disabled，通过 js 脚本都能更改 input 的 value。

### 17. viewport 相关属性？

```html
<meta
	name="viewport"
	content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no"
/>
// width 设置viewport宽度，为一个正整数，或字符串‘device-width’ // device-width
设备宽度 // height
设置viewport高度，一般设置了宽度，会自动解析出高度，可以不用设置 //
initial-scale 默认缩放比例（初始缩放比例），为一个数字，可以带小数 //
minimum-scale 允许用户最小缩放比例，为一个数字，可以带小数 // maximum-scale
允许用户最大缩放比例，为一个数字，可以带小数 // user-scalable 是否允许手动缩放
```
