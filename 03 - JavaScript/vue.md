- [1. 什么是 SPA 单页面？它的优缺点是什么？](#1-什么是-spa-单页面它的优缺点是什么)
- [2. v-show 与 v-if 有什么区别？](#2-v-show-与-v-if-有什么区别)
- [3. Class 与 Style 如何动态绑定？](#3-class-与-style-如何动态绑定)
- [4. 怎样理解 Vue 的单向数据流？](#4-怎样理解-vue-的单向数据流)
- [5. computed 和 watch 的区别和运用的场景？](#5-computed-和-watch-的区别和运用的场景)
- [6. Vue 无法检测怎样的数组变动？如何解决?](#6-vue-无法检测怎样的数组变动如何解决)
- [7. 谈谈你对 Vue 生命周期的理解？](#7-谈谈你对-vue-生命周期的理解)
- [8. Vue 的父组件和子组件生命周期钩子函数执行顺序？](#8-vue-的父组件和子组件生命周期钩子函数执行顺序)
- [9. 父组件如何监听子组件的生命周期？](#9-父组件如何监听子组件的生命周期)
- [10. 谈谈你对 keep-alive 的了解？](#10-谈谈你对-keep-alive-的了解)
- [11. 组件中的 data 为什么是个函数？](#11-组件中的-data-为什么是个函数)
- [12. v-model 的原理？](#12-v-model-的原理)
- [13. Vue 组件间通信有哪几种方式？](#13-vue-组件间通信有哪几种方式)
- [14. Vue-router 中常用的 hash 和 history 路由模式实现原理?](#14-vue-router-中常用的-hash-和-history-路由模式实现原理)
- [15. Vue 是如何实现数据双向绑定的？](#15-vue-是如何实现数据双向绑定的)
- [16. Vue 框架怎么实现对象和数组的监听？](#16-vue-框架怎么实现对象和数组的监听)
- [17. 虚拟 DOM 的实现原理？](#17-虚拟-dom-的实现原理)

### 1. 什么是 SPA 单页面？它的优缺点是什么？

SPA（single-page application）仅在 Web 页面初始化时加载相应的 HTML、JavaScript 和 CSS。一旦页面加载完成，SPA 不会因为用户的操作而进行页面的重新加载或跳转；取而代之的是利用**路由机制**实现 HTML 内容的变换，UI 与用户的交互，避免页面的重新加载。

**优点：**

- 用户体验好、快，内容的改变不需要重新加载整个页面，避免了不必要的跳转和重复渲染。
- 服务器压力小。
- 前后端职责分离，架构清晰：前端进行交互逻辑，后端负责数据处理。

**缺点：**

- 初次加载耗时多：为实现单页 Web 应用功能及显示效果，需要在加载页面的时候将 JavaScript、CSS 统一加载，部分页面按需加载。
- 前进后退路由管理：由于单页应用在一个页面中显示所有的内容，所以不能使用浏览器的前进后退功能，所有的页面切换需要自己建立堆栈管理。
- SEO 难度较大：由于所有的内容都在一个页面中动态替换显示，所以在 SEO 上其有着天然的弱势。

参考：[vue-router 教程](https://router.vuejs.org/zh/guide/)

### 2. v-show 与 v-if 有什么区别？

v-if 是真正的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建；也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

v-show 就简单得多——**不管初始条件是什么，元素总是会被渲染**，并且只是简单地基于 CSS 的 “display” 属性进行切换。

所以，v-if 适用于在运行时很少改变条件，不需要频繁切换条件的场景；v-show 则适用于需要非常频繁切换条件的场景。

### 3. Class 与 Style 如何动态绑定？

通过对象语法：

```js
<div v-bind:class="{ active: isActive, 'text-danger': hasError }"></div>

data: {
  isActive: true,
  hasError: false
}
```

通过数组语法：

```js
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>

data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

### 4. 怎样理解 Vue 的单向数据流？

所有的 prop 都使得其父子 prop 之间形成了一个单向下行绑定：父级 prop 的更新会向下流动到子组件中，但是反过来则不行。这样会防止从子组件意外改变父级组件的状态，从而导致你的应用的数据流向难以理解。

额外的，每次父级组件发生更新时，子组件中所有的 prop 都将会刷新为最新的值。这意味着你不应该在一个子组件内部改变 prop。如果你这样做了，Vue 会在浏览器的控制台中发出警告。子组件想修改时，只能通过 \$emit 派发一个自定义事件，父组件接收到后，由父组件修改。

### 5. computed 和 watch 的区别和运用的场景？

computed 是计算属性，**依赖其它属性值**，并且 computed 的值有**缓存**，只有它依赖的属性值发生改变，下一次获取 computed 的值时才会重新计算 computed 的值。

watch 更多的是观察的作用，类似于某些数据的监听回调，每当监听的数据变化时都会执行回调进行后续操作。

**运用场景：**

- 当我们需要进行数值计算，并且依赖于其它数据时，应该使用 computed，因为可以利用 computed 的缓存特性，避免每次获取值时，都要重新计算。
- 当我们需要**在数据变化时执行异步或开销较大的操作**时，应该使用 watch，使用 watch 选项允许我们执行异步操作，限制我们执行该操作的频率，并在我们得到最终结果前，设置中间状态。这些都是计算属性无法做到的。

参考：[计算属性和侦听器](https://cn.vuejs.org/v2/guide/computed.html)

### 6. Vue 无法检测怎样的数组变动？如何解决?

- 直接用索引值设置一个数组项：`vm.items[index] = newValue`
- 直接修改数组长度：`vm.items.length = newLength`

```js
//修改数组项的方法
Vue.set(vm.items, index, newValue);
vm.$set(vm.items, index, newValue);
vm.items.splice(index, 1, newValue);

//修改数组长度
vm.items.splice(newLength);
```

**vm.\$set 实现原理：**

- 如果目标是数组，使用 splice 方法。
- 如果目标是对象，对对象属性使用`Object.defineProperty`添加 getter 和 setter ，实现数据劫持。

### 7. 谈谈你对 Vue 生命周期的理解？

Vue 的生命周期指的是组件从创建到销毁的一系列的过程。通过提供的 Vue 在生命周期各个阶段的钩子函数，我们可以很好的在 Vue 的各个生命阶段实现一些操作。Vue 一共有 8 个生命阶段，分别是创建前、创建后、加载前、加载后、更新前、更新后、销毁前和销毁后，每个阶段对应了一个生命周期的钩子函数。

1. beforeCreate：组件实例被创建之初，组件的属性生效之前。
2. created：组件实例已经完全创建，属性也绑定，但真实 dom 还没有生成，\$el 还不可用。我们可以在这里进行 **Ajax 请求**。
3. beforeMount：此时已经完成了模板的编译，但是还没有挂载到页面中，相关的 render 函数首次被调用。
4. mounted：此时，已经将编译好的模板，挂载到了页面指定的容器中显示，此时真实 DOM 渲染完了，可以**操作 DOM 了**。
5. beforeUpdate：状态更新之前执行此函数， 此时 data 中的状态值是最新的，但是界面上显示的数据还是旧的，因为此时还没有开始重新渲染 DOM 节点。
6. updated：实例更新完毕之后调用此函数，此时 data 中的状态值和界面上显示的数据，都已经完成了更新，界面已经被重新渲染好了。
7. beforeDestroy：实例销毁之前调用。在这一步，实例仍然完全可用，可以这时**清除定时器或清除事件绑定**。
8. destroyed：Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。

![Vue 生命周期示意图](https://camo.githubusercontent.com/35d63eb1f11390dc47f709e86ab7806821d48c9c/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303631315f323133302e706e67)

### 8. Vue 的父组件和子组件生命周期钩子函数执行顺序？

- 加载渲染过程

父 beforeCreate -> 父 created -> 父 beforeMount -> 子 beforeCreate -> 子 created -> 子 beforeMount -> 子 mounted -> 父 mounted

- 子组件更新过程

父 beforeUpdate -> 子 beforeUpdate -> 子 updated -> 父 updated

- 父组件更新过程

父 beforeUpdate -> 父 updated

- 父 beforeDestroy -> 子 beforeDestroy -> 子 destroyed -> 父 destroyed

### 9. 父组件如何监听子组件的生命周期？

```js
// 方法一：使用$emit触发父组件的事件
// Parent.vue
<Child @mounted="doSomething" />

// Child.vue
mounted(){
    this.$emit("mounted");
}

// 方法二：使用hook监听
// Parent.vue
<Child @hook:mounted="doSomething" />

doSomething(){
    console.log('父组件监听到 mounted 钩子函数 ...');
}

// Child.vue
mounted(){
    console.log('子组件触发 mounted 钩子函数 ...');
}
```

### 10. 谈谈你对 keep-alive 的了解？

keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，避免重新渲染 ，其有以下特性：

- 一般结合路由和动态组件一起使用，用于缓存组件。
- 提供 include 和 exclude 属性，两者都支持字符串或正则表达式， include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的组件都不会被缓存 ，其中 exclude 的优先级比 include 高。
- 对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated。

### 11. 组件中的 data 为什么是个函数？

因为组件是用来复用的，且 JS 里对象是引用关系，如果组件中 data 是一个对象，那么这样作用域没有隔离，子组件中的 data 属性值会相互影响，如果组件中 data 选项是一个函数，那么**每个实例可以维护一份被返回对象的独立的拷贝，组件实例之间的 data 属性值不会互相影响**；而 new Vue 的实例，是不会被复用的，因此不存在引用对象的问题。

### 12. v-model 的原理？

我们在 vue 项目中主要使用 v-model 指令在表单 input、textarea、select 等元素上创建双向数据绑定，我们知道 v-model 本质上不过是语法糖，v-model 在内部为不同的输入元素使用不同的属性并抛出不同的事件：

- text 和 textarea 元素使用 value 属性和 input 事件
- checkbox 和 radio 使用 checked 属性和 change 事件
- select 字段将 value 作为 prop 并将 change 作为事件

```js
<input v-model="something" />

//等价于
<input v-bind:value="something" v-on:input="something = $event.target.value" />
```

在自定义组件中，v-model 默认会利用名为 value 的 prop 和名为 input 的事件：

```js
//父组件：
<Child v-model="message"></Child>

//子组件：
<div>{{value}}</div>

props:{
    value: String
},
methods: {
  test(){
     this.$emit('input', '小红')
  }
}
```

### 13. Vue 组件间通信有哪几种方式？

Vue 组件间通信只要指以下 3 类通信：父子组件通信、隔代组件通信、兄弟组件通信，下面我们分别介绍每种通信方式且会说明此种方法可适用于哪类组件间通信。

1. props / \$emit 适用父子组件通信
2. ref 与 \$parent / \$children 适用父子组件通信
3. EventBus （\$emit / \$on） 适用于父子、隔代、兄弟组件通信
4. \$attrs/\$listeners 适用于隔代组件通信
5. provide / inject 适用于隔代组件通信
6. Vuex 适用于 父子、隔代、兄弟组件通信

参考：[Vue 组件间通信六种方式](https://juejin.im/post/6844903845642911752)

### 14. Vue-router 中常用的 hash 和 history 路由模式实现原理?

**hash 模式实现原理**

hash 就是 url 中 # 后面的内容。

- URL 中 hash 值只是客户端的一种状态，也就是说当向服务器端发出请求时，hash 部分不会被发送。
- hash 值的改变，都会在浏览器的访问历史中增加一个记录。因此我们能通过浏览器的回退、前进按钮控制 hash 的切换。
- 可以通过 a 标签，并设置 href 属性，当用户点击这个标签后，URL 的 hash 值会发生改变。
- 可以使用 hashchange 事件来监听 hash 值的变化，从而对页面进行跳转（渲染）。

**history 模式的实现原理**

HTML5 提供了 History API 来实现 URL 的变化。最主要的 API 有以下两个：`history.pushState()`和`history.repalceState()`。这两个 API 可以在不进行刷新的情况下，操作浏览器的历史纪录。

- pushState 和 repalceState 两个 API 来操作实现 URL 的变化。
- 可以使用 popstate 事件来监听 url 的变化，从而对页面进行跳转（渲染）。
- pushState 或 replaceState 不会触发 popstate 事件，这时我们需要手动触发页面跳转（渲染）。

### 15. Vue 是如何实现数据双向绑定的？

Vue 数据双向绑定主要是指：数据变化更新视图，视图变化更新数据。

视图变化更新数据可以通过事件监听的方式来实现，比如 input 标签的 oninput 事件，当 input 的 value 值发生变化就会触发。

数据变化更新视图主要通过使用数据劫持和发布订阅者模式来实现的。用一句话概括：使用`Object.defineProperty`方法把 data 对象里的每个数据的读写转化成 getter/setter，当数据变化时通知视图更新。

第一步，实现一个监听器，用来劫持并监听所有属性，如果属性发生变化，就通知订阅者。使用`Object.defineProperty`方法把 data 对象里的每个数据的读写转化成 getter/setter，当数据变化就会触发 setter，这样就监听到了数据变化。

第二步，实现一个订阅器，用来收集订阅者，对监听器和订阅者进行统一管理。

第三步，实现一个订阅者，收到属性的变化通知并执行相应的方法，从而更新视图。

第四步，实现一个解析器，解析每个节点的相关指令，对模板数据和订阅器进行初始化。

参考：[0 到 1 掌握：Vue 核心之数据双向绑定](https://juejin.im/post/6844903903822086151)

### 16. Vue 框架怎么实现对象和数组的监听？

遍历数组和递归遍历对象，使用`Object.defineProperty()`对数据进行劫持。

### 17. 虚拟 DOM 的实现原理？

- 第一步，使用 js 对象模拟真实 dom 树。
- 第二步，比较修改前后两棵虚拟 dom 树的差异。（diff 算法）
- 第三步，将差异应用到真实 dom 树，更新对应节点。（pach 算法）

参考：[深入剖析：Vue 核心之虚拟 DOM](https://juejin.im/post/6844903895467032589#heading-14)
