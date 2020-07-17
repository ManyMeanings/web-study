- [HTML 骨架](#html-骨架)
- [HTML 常用标签](#html-常用标签)
- [HTML 表格](#html-表格)
- [HTML 表单](#html-表单)
  - [`<form></form>`](#formform)
  - [`<input />`](#input-)
  - [`<select></select>`](#selectselect)
  - [`<textarea></textarea>`](#textareatextarea)
  - [`<label></label>`](#labellabel)
  - [表单的语义化](#表单的语义化)
- [特殊字符](#特殊字符)
- [HTML5 新增内容](#html5-新增内容)
  - [语义标签](#语义标签)
  - [表单](#表单)
    - [`<input />`新增类型](#input-新增类型)
    - [表单属性](#表单属性)
    - [`<datalist>` 数据列表](#datalist-数据列表)
    - [`<keygen>`](#keygen)
    - [表单事件](#表单事件)
  - [`<audio></audio>`](#audioaudio)
  - [`<video></video>`](#videovideo)
  - [拖拽](#拖拽)
  - [历史](#历史)
  - [存储](#存储)

## HTML 骨架

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body></body>
</html>
```

## HTML 常用标签

- `<h1></h1>`：标题，h1 最大，h6 最小。
- `<p></p>`：段落，**文本级标签（只能放文字、图片、表单元素）**。
- `<br />`：换行。
- `<div></div>`：分割。
- `<span></span>`：范围、跨度，**文本级标签**。
- `<pre></pre>`：预格式化，保留排版。
- `<sup></sup>`和`<sub></sub>`：上标和下标。
- `<a href="url" title="悬停文本" target="_self/_blank/_parent/_top"></a>`：超链接，**文本级标签**。
- `<img src="url" alt="图片不可用时替代的文本" title=“悬停文本” />`：图片
- `<ul></ul>`和`<ol></ol>`：无序列表和有序列表，列表项`<li></li>`。
- `<dl></dl>`、`<dt></dt>`和`<dd></dd>`：定义列表、列表标题和列表项。
- `<iframe src="url" scrolling="no" ></iframe>`：内嵌框架。

## HTML 表格

**使用`<thead>`、`<tbody>`、`<tfoot>`的好处：**

- 三部分的代码顺序可以任意，否则浏览器从上到下显示。
- 当表格数据量大的时候，数据可以边获取边显示。

```html
<table>
  <caption>
    How I chose to spend my money
  </caption>
  <thead>
    <tr>
      <th>Purchase</th>
      <th>Location</th>
      <th>Date</th>
      <th>Evaluation</th>
      <th>Cost (€)</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td colspan="4">SUM</td>
      <td>118</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Haircut</td>
      <td>Hairdresser</td>
      <td>12/09</td>
      <td>Great idea</td>
      <td>30</td>
    </tr>
    ...
    <tr>
      <td>Toothpaste</td>
      <td>Supermarket</td>
      <td>13/09</td>
      <td>Good</td>
      <td>5</td>
    </tr>
  </tbody>
</table>

<style>
  html {
    font-family: sans-serif;
  }

  table {
    border-collapse: collapse;
    border: 2px solid rgb(200, 200, 200);
    letter-spacing: 1px;
    font-size: 0.8rem;
  }

  td,
  th {
    border: 1px solid rgb(190, 190, 190);
    padding: 10px 20px;
  }

  th {
    background-color: rgb(235, 235, 235);
  }

  td {
    text-align: center;
  }

  tr:nth-child(even) td {
    background-color: rgb(250, 250, 250);
  }

  tr:nth-child(odd) td {
    background-color: rgb(245, 245, 245);
  }

  caption {
    padding: 10px;
  }
</style>
```

## HTML 表单

### `<form></form>`

属性：

- `name`：表单的名称，用于 JS 来操作或控制表单时使用。
- `id`：表单的名称，用于 JS 来操作或控制表单时使用。
- `action`：指定表单数据的处理程序，一般是 PHP，如：action=“login.php”。
- `method`：表单数据的提交方式，一般取值：get(默认)和 post。
- `enctype`：默认值：`application/x-www-form-urlencoded`，提交文件：`multipart/form-data`

### `<input />`

属性：

- `type`：
  - `text`：默认。
  - `password`：密码类型。
  - `radio`：单选按钮，`name`属性相同的按钮作为一组进行单选。设置`checked`默认处于选中状态。
  - `checkbox`：多选按钮，`name`属性相同的按钮作为一组进行多选。设置`checked`默认处于选中状态。
  - `button`：普通按钮，结合 js 代码使用。
  - `submit`：提交按钮，传送当前表单的数据给服务器或其他程序处理。
  - `file`：选择文件。
  - `reset`：重置按钮，清空当前表单内容，并设置为默认值。
  - `image`：图片按钮，和提交按钮的功能一致，不过可以显示图片。
  - `hidden`：隐藏。
- `value`：文本框里的默认内容。
- `size="50"`：表示文本框内可以显示五十个字符，一个英文或一个中文都算一个字符。
- `readonly`：文本框只读，不能编辑。
- `disabled`：文本框只读，不能编辑。

### `<select></select>`

下拉列表，每一项用`<option></option>`表示。

属性;

- `multiple`：可以对下拉列表中的选项进行多选,写成`multiple=""`。
- `size="3"`：如果属性值大于 1，则列表为滚动视图。默认属性值为 1，即下拉视图。

`<option></option>`的属性：

- `selected`：默认选中。

### `<textarea></textarea>`

属性：

- `row="4"`：文本区域的行数为 4。
- `cols=20`：文本区域的列数为 20。
- `readonly`：只读。

### `<label></label>`

点击`label`同时将焦点移到绑定的表单元素上。让`label`标签的`for`属性值，和 `input`标签的`id`属性值相同，那么这个`label`和`input`就有绑定关系了。

### 表单的语义化

`<fieldset></fieldset>`用来划分区域，`<legend></legend>`为区域的标题。

## 特殊字符

- `&nbsp;` ：空格
- `&lt;`：小于号
- `&gt;`：大于号
- `&amp;`：符号`&`

## HTML5 新增内容

### 语义标签

- `<section>` 表示区块
- `<article>` 表示文章
- `<header>` 表示页眉
- `<footer>` 表示页脚
- `<nav>` 表示导航
- `<aside>` 表示侧边栏
- `<figure>` 表示媒介内容分组
- `<time>` 表示日期

**HTML5 经典布局**

```html
<header>
  <ul class="nav"></ul>
</header>

<div class="main">
  <article></article>
  <aside></aside>
</div>

<footer></footer>
```

### 表单

#### `<input />`新增类型

- `email`：只能输入 email 格式
- `tel`：手机号码
- `url`：只能输入 url 格式
- `number`：只能输入数字
- `search`：搜索框
- `range`：滑动条
- `color`：拾色器
- `time`：时间
- `date`：日期
- `datetime`：时间日期
- `month`：月份
- `week`：星期

#### 表单属性

- `placeholder` 占位符（提示文字）
- `autofocus` 自动获取焦点
- `multiple` 文件上传多选或多个邮箱地址
- `autocomplete` 自动完成（填充的）。on 开启（默认），off 取消。
- `form` 指定表单项属于哪个 form，处理复杂表单时会需要
- `novalidate` 关闭默认的验证功能（只能加给 form）
- `required` 表示必填项
- `pattern` 自定义正则，验证表单

#### `<datalist>` 数据列表

```html
<input type="text" list="myData" />
<datalist id="myData">
  <option>本科</option>
  <option>研究生</option>
  <option>不明</option>
</datalist>
```

#### `<keygen>`

keygen 元素是密钥对生成器。当提交表单时，会生成两个键：一个公钥，一个私钥。

私钥存储于客户端，公钥则被发送到服务器。公钥可用于之后验证用户的客户端证书。

#### 表单事件

- `oninput()`：用户输入内容时触发。
- `oninvalid()`：验证不通过时触发。

### `<audio></audio>`

属性：

- `autoplay`：自动播放
- `controls`：控制条
- `loop`：循环播放
- `preload`：预加载

```html
<audio controls loop>
  <source src="music/yinyue.mp3" />
  <source src="music/yinyue.ogg" />
  <source src="music/yinyue.wav" />
  抱歉，你的浏览器暂不支持此音频格式
</audio>
```

### `<video></video>`

属性：

- `autoplay` 自动播放
- `controls` 控制条
- `loop` 循环播放
- `preload` 预加载

```html
<video controls autoplay>
  <source src="video/movie.mp4" />
  <source src="video/movie.ogg" />
  <source src="video/movie.webm" />
  抱歉，不支持此视频
</video>
```

### 拖拽

在 HTML5 的规范中，我们可以通过为元素增加`draggable="true"`来设置此元素是否可以进行拖拽操作，其中图片、链接默认是开启拖拽的。

**拖拽元素的事件监听：**

- `ondragstart`：当拖拽开始
- `ondragleave`：当鼠标离开拖拽元素
- `ondragend`：当拖拽结束
- `ondrag`：整个拖拽过程都会调用

**目标元素的事件监听：**

- `ondragenter`：当拖拽元素进入
- `ondragover`：当拖拽元素停留在目标元素上，连续触发（配合`event.preventDefault()`使用）
- `ondrop`：当在目标元素上松开鼠标
- `ondragleave`：当鼠标离开目标元素

### 历史

`window.history`对象可以让我们管理历史记录，可用于单页面应用，可以无刷新改变网页内容。

- `window.history.forward()`：前进
- `window.history.back()`：后退
- `window.history.go(n)`：n=1 表示前进；n=-1 后退；n=0s 刷新。如果移动的位置超出了访问历史的边界，会静默失败，但不会报错。

### 存储

随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性在本地存储大量的数据，传统方式我们以 document.cookie 来进行存储的，但是由于其存储大小只有 4k 左右，并且解析也相当的复杂，给开发带来诸多不便，HTML5 规范则提出解决方案：`window.sessionStorage`和`window.localStorage`。

- `setItem(key, value)`
- `getItem(key)`
- `removeItem(key)`
- `clear()`
- `key()`;

```html
<!--案例：记住用户名密码-->
<!DOCTYPE html>
<html>
  <head lang="en">
    <meta charset="UTF-8" />
    <title></title>
  </head>
  <body>
    <label for=""> 用户名：<input type="text" class="userName" /> </label>
    <br /><br />
    <label for=""> 密 码：<input type="text" class="pwd" /> </label>
    <br /><br />
    <label for="">
      <input type="checkbox" class="check" id="" />记住密码
    </label>
    <br /><br />
    <button>登录</button>

    <script>
      var userName = document.querySelector(".userName");
      var pwd = document.querySelector(".pwd");
      var chk = document.querySelector(".check");
      var btn = document.querySelector("button");

      //当点击登录的时候 如果勾选“记住密码”，就存储密码；否则就清除密码
      btn.onclick = function () {
        if (chk.checked) {
          //记住数据
          window.localStorage.setItem("userName", userName.value);
          window.localStorage.setItem("pwd", pwd.value);
        } else {
          //清除数据
          window.localStorage.removeItem("userName");
          window.localStorage.removeItem("pwd");
        }
      };
      //下次登录时，如果记录的有数据，就直接填充
      window.onload = function () {
        userName.value = window.localStorage.getItem("userName");
        pwd.value = window.localStorage.getItem("pwd");
      };
    </script>
  </body>
</html>
```
