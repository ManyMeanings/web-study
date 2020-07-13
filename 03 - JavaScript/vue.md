- [基础](#基础)
  - [Vue.js 介绍](#vuejs-介绍)
    - [Vue 框架的特点](#vue-框架的特点)
    - [MVVM 模式](#mvvm-模式)
  - [安装](#安装)
    - [使用`<script>`直接引入](#使用script直接引入)
    - [NPM](#npm)
    - [vue-cli](#vue-cli)
  - [Vue 实例](#vue-实例)
    - [创建一个 Vue 实例](#创建一个-vue-实例)
    - [数据与方法](#数据与方法)
    - [实例生命周期钩子](#实例生命周期钩子)
  - [模板语法](#模板语法)
    - [插值](#插值)
    - [指令](#指令)
    - [参数](#参数)
    - [修饰符](#修饰符)
    - [缩写](#缩写)
  - [计算属性和侦听器](#计算属性和侦听器)
    - [计算属性](#计算属性)
    - [计算属性和方法的不同](#计算属性和方法的不同)
    - [计算属性对比侦听属性](#计算属性对比侦听属性)
    - [计算属性的 setter](#计算属性的-setter)
  - [侦听器](#侦听器)
  - [Class 与 Style 绑定](#class-与-style-绑定)
    - [绑定 HTML Class](#绑定-html-class)
    - [绑定内联样式](#绑定内联样式)
  - [条件渲染](#条件渲染)
    - [v-if](#v-if)
    - [v-show](#v-show)
  - [列表渲染](#列表渲染)
    - [v-for](#v-for)
  - [事件处理](#事件处理)
    - [v-on](#v-on)
    - [事件修饰符](#事件修饰符)
    - [为什么在 HTML 中监听事件？](#为什么在-html-中监听事件)
  - [表单输入绑定](#表单输入绑定)
    - [v-model](#v-model)
    - [值绑定](#值绑定)
    - [修饰符](#修饰符-1)
  - [组件基础](#组件基础)

# 基础

## Vue.js 介绍

Vue 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

### Vue 框架的特点

- 模板渲染
- 响应式的更新机制
- 渐进式框架
- 组件化/模块化
- 轻量，速度快

### MVVM 模式

- Model：负责数据存储
- View：负责页面展示
- View Model：负责业务逻辑处理，对数据加工后交给视图展示

## 安装

### 使用`<script>`直接引入

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

### NPM

在用 Vue 构建大型应用时推荐使用 NPM 安装。NPM 能很好地和诸如 webpack 或 Browserify 模块打包器配合使用。同时 Vue 也提供配套工具来开发单文件组件。

```bash
npm install vue
```

```js
import Vue from "vue";
```

### vue-cli

## Vue 实例

### 创建一个 Vue 实例

每个 Vue 应用都是通过用 Vue 函数创建一个新的 Vue 实例开始的：

```js
var vm = new Vue({
  //绑定元素
  el: "",
  //绑定数据
  data: {},
  //绑定方法
  methods: {},
});
```

### 数据与方法

当一个 Vue 实例被创建时，它将 data 对象中的所有的 property 加入到 Vue 的响应式系统中。当这些 property 的值发生改变时，视图将会产生“响应”，即匹配更新为新的值。

```js
var data = {
  a: 1,
};
var vm = new Vue({
  data: data,
});
console.log(vm.a == data.a); // => true

vm.a = 2;
console.log(data.a); // => 2

data.a = 3;
console.log(vm.a); // => 3
```

只有当实例被创建时就已经存在于 data 中的 property 才是响应式的。如果你知道你会在晚些时候需要一个 property，但是一开始它为空或不存在，那么你需要设置一些初始值。但是，如果使用了 Object.freeze()，这会阻止修改现有的 property，也意味着响应系统无法再追踪变化。

```js
var obj = {
  foo: "bar",
};
Object.freeze(obj);
```

除了数据 property，Vue 实例还暴露了一些有用的实例 property 与方法。它们都有前缀 \$，以便与用户定义的 property 区分开来。例如：

```js
var data = { a: 1 };
var vm = new Vue({
  el: "#example",
  data: data,
});

vm.$data === data; // => true
vm.$el === document.getElementById("example"); // => true

// $watch 是一个实例方法
vm.$watch("a", function (newValue, oldValue) {
  // 这个回调将在 `vm.a` 改变后调用
});
```

### 实例生命周期钩子

每个 Vue 实例在被创建时都要经过一系列的初始化过程，这个过程中也会运行一些叫做生命周期钩子的函数，这给了用户在不同阶段添加自己的代码的机会，例如：

```js
new Vue({
  data: {
    a: 1,
  },
  created: function () {
    //this指向调用它的 Vue 实例
    console.log(this.a);
  },
});
```

![](https://cn.vuejs.org/images/lifecycle.png)

## 模板语法

Vue.js 使用了基于 HTML 的模板语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。所有 Vue.js 的模板都是合法的 HTML，所以能被遵循规范的浏览器和 HTML 解析器解析。

在底层的实现上，Vue 将模板编译成虚拟 DOM 渲染函数。结合响应系统，Vue 能够智能地计算出最少需要重新渲染多少组件，并把 DOM 操作次数减到最少。

### 插值

```html
<!--文本-->
<span>{{msg}}</span>

<!--html-->
<span v-html="rawHtml"></span>

<!--Attribute-->
<span v-bind:class="dynamicClass"></span>

<!--js 表达式-->
{{ number + 1 }} {{ ok ? 'YES' : 'NO' }} {{ message.split('').reverse().join('')
}}

<div v-bind:id="'list-' + id"></div>
```

### 指令

指令是带有 v- 前缀的特殊 attribute。指令 attribute 的值预期是单个 JavaScript 表达式。指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM。

### 参数

一些指令能够接收一个“参数”，在指令名称之后以冒号表示。

```html
<button v-on:click="click"></button>

<!--动态参数 使用js 表达式-->
<button v-on:[eventName]="doSomething"></button>
```

### 修饰符

修饰符是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：

```html
<form v-on:submit.prevent="onSubmit"></form>
```

### 缩写

Vue 为 v-bind 和 v-on 这两个最常用的指令，提供了特定简写：

```html
<!-- 缩写 -->
<a :href="url"></a>

<!-- 动态参数的缩写 (2.6.0+) -->
<a :[key]="url"></a>

<!-- 缩写 -->
<a @click="doSomething"></a>

<!-- 动态参数的缩写 (2.6.0+) -->
<a @[event]="doSomething"></a>
```

## 计算属性和侦听器

### 计算属性

模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。所以，对于任何复杂逻辑，你都应当使用计算属性。

```js
var vm = new Vue({
  el: "#example",
  data: {
    msg: "Hello",
  },
  computed: {
    reversedMsg: function () {
      return this.msg.split("").reverse().join("");
    },
  },
});

console.log(vm.reversedMsg); // => olleH
```

### 计算属性和方法的不同

我们可以将同一函数定义为一个方法而不是一个计算属性。两种方式的最终结果确实是完全相同的。然而，不同的是**计算属性是基于它们的响应式依赖进行缓存的**。只在相关响应式依赖发生改变时它们才会重新求值。这就意味着只要 msg 还没有发生改变，多次访问 reversedMsg 计算属性会立即返回之前的计算结果，而不必再次执行函数。相比之下，每当触发重新渲染时，调用方法将总会再次执行函数。

### 计算属性对比侦听属性

Vue 提供了一种更通用的方式来观察和响应 Vue 实例上的数据变动：侦听属性。当你有一些数据需要随着其它数据变动而变动时，你很容易滥用 watch。然而，通常更好的做法是使用计算属性而不是命令式的 watch 回调。

### 计算属性的 setter

计算属性默认只有 getter，不过在需要时你也可以提供一个 setter：

```js
// ...
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName;
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ');
      this.firstName = names[0];
      this.lastName = names[names.length - 1];
    }
  }
}
// ...
//调用setter
vm.fullName = "John Doe";
```

## 侦听器

虽然计算属性在大多数情况下更合适，但有时也需要一个自定义的侦听器。这就是为什么 Vue 通过 watch 选项提供了一个更通用的方法，来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

```html
<!--访问一个api-->
<div id="watch-example">
  <p>
    Ask a yes/no question:
    <input v-model="question" />
  </p>
  <p>{{answer}}</p>
</div>

<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lodash@4.13.1/lodash.min.js"></script>
<script>
  var watchExampleVM = new Vue({
    el: "#watch-example",
    data: {
      question: "",
      answer: "I cannot give you an answer until you ask a question!",
    },
    watch: {
      // 如果 `question` 发生改变，这个函数就会运行
      question: function (newQuestion, oldQuestion) {
        this.answer = "Waiting for you to stop typing...";
        this.debouncedGetAnswer();
      },
    },
    created: function () {
      // `_.debounce` 是一个通过 Lodash 限制操作频率的函数。
      this.debouncedGetAnswer = _.debounce(this.getAnswer, 500);
    },
    methods: {
      getAnswer: function () {
        if (this.question.indexOf("?") === -1) {
          this.answer = "Questions usually contain a question mark. ";
          return;
        }
        this.answer = "Thinking...";
        var vm = this;
        axios
          .get("https://yesno.wtf/api")
          .then(function (response) {
            vm.answer = _.capitalize(response.data.answer);
          })
          .catch(function (error) {
            vm.answer = "Error! Could not reach the API. " + error;
          });
      },
    },
  });
</script>
```

## Class 与 Style 绑定

操作元素的 class 列表和内联样式是数据绑定的一个常见需求。因为它们都是 attribute，所以我们可以用 v-bind 处理它们：只需要通过表达式计算出字符串结果即可。不过，字符串拼接麻烦且易错。因此，在将 v-bind 用于 class 和 style 时，Vue.js 做了专门的增强。表达式结果的类型除了字符串之外，还可以是对象或数组。

### 绑定 HTML Class

```html
<!--1. 对象语法-->
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>

data: { isActive: true, hasError: false }

<!--以上代码渲染结果是：-->
<div class="static active"></div>

<!--2. 数组语法-->
<div v-bind:class="[activeClass, errorClass]"></div>

data: { activeClass: 'active', errorClass: 'text-danger' }

<!--以上代码渲染结果是：-->
<div class="active text-danger"></div>
```

### 绑定内联样式

```html
<!--1. 对象语法-->
<div v-bind:style="styleObject"></div>

data: { styleObject: { color: 'red', fontSize: '13px' } }

<!--2. 数组语法-->
<!--将多个样式对象应用到同一个元素上-->
<div v-bind:style="[baseStyles, overridingStyles]"></div>

<!--多重值 2.3.0+ -->
<!--这样写只会渲染数组中最后一个被浏览器支持的值。-->
<div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>
```

## 条件渲染

### v-if

v-if 指令用于条件性地渲染一块内容。这块内容只会在指令的表达式返回 truthy 值的时候被渲染。也可以用 v-else 添加一个“else 块”,用 v-else-if 充当 v-if 的“else-if 块”：

```html
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>

<!--用 template 渲染分组-->
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。这样也不总是符合实际需求，所以 Vue 为你提供了一种方式来表达“这两个元素是完全独立的，不要复用它们”。只需添加一个具有唯一值的 key attribute 即可：

```html
<template v-if="loginType === 'username'">
  <label>Username</label>
  <input placeholder="Enter your username" key="username-input" />
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Enter your email address" key="email-input" />
</template>
```

### v-show

另一个用于根据条件展示元素的选项是 v-show 指令,用法和 v-if 大致一样，但是 v-show 不支持 <template> 元素，也不支持 v-else。

**v-if 和 v-show 的区别**

v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。

## 列表渲染

### v-for

```html
<!--基于数组-->
<ul id="example-1">
  <li v-for="(item, index) in items" v-bind:key="item.msg">
    {{item.msg}}
  </li>
</ul>

<script>
  var example1 = new Vue({
    el: "#example-1",
    data: { items: [{ msg: "foo" }, { msg: "bar" }] },
  });
</script>

<!--基于对象-->
<ul id="example-2">
  <li v-for="(value, name, index) in object" v-bind:key="value">
    {{ index }}. {{ name }}: {{ value }}
  </li>
</ul>

<script>
  new Vue({
    el: "#example-2",
    data: {
      object: {
        title: "How to do lists in Vue",
        author: "Jane Doe",
        publishedAt: "2016-04-10",
      },
    },
  });
</script>

<!--在 template 上使用-->
<ul>
  <template v-for="item in items">
    <li>{{ item.msg }}</li>
    <li class="divider" role="presentation"></li>
  </template>
</ul>
```

当 Vue 正在更新使用 v-for 渲染的元素列表时，它默认使用“就地更新”的策略。如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序，而是就地更新每个元素，并且确保它们在每个索引位置正确渲染。这个默认的模式是高效的，但是只适用于不依赖子组件状态或临时 DOM 状态（例如：表单输入值）的列表渲染输出。

为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 key attribute。建议尽可能在使用 v-for 时提供 key attribute，除非遍历输出的 DOM 内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。

## 事件处理

### v-on

```html
<div id="example">
  <button v-on:click="greet">Greet</button>
</div>

<script>
  var example = new Vue({
    el: "example",
    data: {
      name: "Vue.js",
    },
    methods: {
      greet: function (event) {
        alert("hello");
        if (event) {
          alert(event.target.tagName);
        }
      },
    },
  });
</script>
```

### 事件修饰符

```html
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即内部元素触发的事件先在此处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
```

### 为什么在 HTML 中监听事件？

你可能注意到这种事件监听的方式违背了关注点分离这个长期以来的优良传统。但不必担心，因为所有的 Vue.js 事件处理方法和表达式都严格绑定在当前视图的 ViewModel 上，它不会导致任何维护上的困难。实际上，使用 v-on 有几个好处：

1. 扫一眼 HTML 模板便能轻松定位在 JavaScript 代码里对应的方法。
2. 因为你无须在 JavaScript 里手动绑定事件，你的 ViewModel 代码可以是非常纯粹的逻辑，和 DOM 完全解耦，更易于测试。
3. 当一个 ViewModel 被销毁时，所有的事件处理器都会自动被删除。你无须担心如何清理它们。

## 表单输入绑定

### v-model

你可以用 v-model 指令在表单`<input>`、`<textarea>`及`<select>`元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇，但 v-model 本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。

v-model 会忽略所有表单元素的 value、checked、selected attribute 的初始值而总是将 Vue 实例的数据作为数据来源。你应该通过 JavaScript 在组件的 data 选项中声明初始值。

```html
<!--文本-->
<input v-model="message" placeholder="edit me" />
<p>Message is: {{ message }}</p>

<!--多行文本-->
<p>{{ message }}</p>
<textarea v-model="message" placeholder="add multiple lines"></textarea>

<!--复选框-->
<input type="checkbox" id="checkbox" v-model="checked" />
<label for="checkbox">{{ checked }}</label>

<!--单选按钮-->
<div id="example">
  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>
  <br />
  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>
  <br />
  <span>Picked: {{ picked }}</span>
</div>

<!--选择框-->
<div id="example-6">
  <select v-model="selected" multiple style="width: 50px;">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <br />
  <span>Selected: {{ selected }}</span>
</div>
```

### 值绑定

有时我们可能想把值绑定到 Vue 实例的一个动态 property 上，这时可以用 v-bind 实现，并且这个 property 的值可以不是字符串。

### 修饰符

- .lazy 在 change 事件之后进行同步
- .number 自动将用户的输入值转为数值类型
- .trim 自动过滤用户输入的首尾空白字符

## 组件基础
