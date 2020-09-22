# JavaScript 笔记

- JavaScript 是一种动态类型语言，使用`let`和`var`声明的变量可以随时重新赋值为其他类型的值。
- 标识符命名规则：
  - 第一个字符，可以是任意 Unicode 字母（包括中文），美元符号和下划线；
  - 后面的字符除了以上三种还可以是数字；
  - 不能为保留字。
- 对于`var`命令来说，JavaScript 的区块不构成单独的作用域。


  ## 数据类型

- 自动转为`false`的值：`undefined`，`null`，`false`，`0`，`NaN`，`""`（**注意：空数组，空对象和只有空格的字符串都自动转为`true`**）

- JavaScript 内部，所有数字都是以64位浮点数形式储存，即使是整数也是如此。`1 === 1.0 // true`

- 全局方法`parseInt`规则：

  - 如果字符串头尾有空格，自动去除（`Number()`也是如此）；
  - 如果不是字符串，则先转为字符串再转换，从左至右遇到不能转为数字的字符时停止，如果最高位无法转换，返回`NaN`（不包括正负号接数字的情况）。

- 字符串是类数组，无法直接通过索引改变单个字符，也无法改变`length`属性。

- 对象的所有键名都是字符串（ES6 引入Symbol 也可以作为键名），所以加不加引号都可以，如果键名是数值，会自动转为字符串。如果键名不是数值也不满足标识符的规则同时也没有加引号，会报错。

- ```js
  const obj = {
    name: 'Rick',
    age: 21
  }
  // 删除对象本身的属性
  delete obj.age // true
  
  // 属性是否存在（包括继承的属性）
  'name' in  obj // true
  ```

- ```js
  const fn = function(a, b){
    return a + b;
  }
  fn.name // 'fn'
  
  // 定义时函数的参数个数
  fn.length // 2
  ```

- 函数的作用域就是其声明时所在的作用域，与运行时的作用域无关。

- `arguments`对象是一个类数组，包含函数运行时的所有对象，可读可写，但是在严格模式下与实际函数参数不具有联动关系。

- 闭包就是能够读取其他函数内部变量的函数，可以简单理解成定义在一个函数内部的函数。闭包除了能在函数外读取函数内部的变量以及封装私有属性和方法，还可以让这些变量始终保持在内存中，记住上一次调用时的运算结果。

- 立即执行函数的好处：避免污染全局变量。

- 清空数组的一个有效方法就是将`length`设为0。

## 运算符

- 数值运算符（+）可以将任何值转为数值，与`Number()`的作用相同。

- ```js
  1 === 0x1 // true
  NaN === NaN  // false
  +0 === -0 // true
  {} === {} // false
  ```

- 逗号运算符用于对两个表达式求值，并返回后一个表达式的值，主要用于在返回一个值之前进行一些辅助操作。

- 赋值运算符（`=`），三元条件运算符（`?:`）和指数运算符（`**`）是右结合运算符。

- ```js
  // 布尔值：true 转成 1，false 转成 0
  Number(true) // 1
  Number(false) // 0
  
  // 转为0的情况
  Number('') // 0
  Number(null) // 0
  
  // 转为 NaN 的情况
  Number('324abc') // NaN
  Number(undefined) // NaN
  Number({a: 1}) // NaN
  ```

## 标准库

### Object

- 如果参数是原始类型的值，`Object`方法将其转为对应的包装对象的实例；如果参数是一个对象，它总是返回该对象，与`Object`构造函数基本相同，只是语意不同。

- ```js
  const obj = {
    p1: 123,
    p2: 'word'
  };
  
  // 遍历对象的属性，第二种方法还会返回不可枚举的属性名
  Object.keys(obj) // ["p1", "p2"]
  Object.getOwnPropertyNames(obj) // ["p1", "p2"]
  
  // 返回对象的值，自动类型转换会调用这个方法，默认返回对象本身
  obj === obj.valueOf() // true
  //判断对象是否具有某个属性
  obj.hasOwnProperty('p1') // true
  ```

- 每个对象的属性都有自己对应的属性描述对象，保存该属性的一些元信息：

  - `value`：属性值
  - `writable`：是否可写
  - `enumerable`：是否可遍历
  - `configurable`：属性描述对象的可写性
  - `get`：该属性的取值函数
  - `set`：该属性的存值函数

- ```js
  const obj = { p: 'a' };
  
  // 获取属性描述对象
  Object.getOwnPropertyDescriptor(obj, 'p');
  // Object { value: "a",
  //   writable: true,
  //   enumerable: true,
  //   configurable: true
  // }
  
  // 定义或修改某个属性的属性描述对象，返回修改后的对象
  const obj2 = Object.defineProperty({}, 'p', {
    value: 123,
    writable: false,
    enumerable: true,
    configurable: false
  });
  const obj3 = Object.defineProperties({}, {
    p1: { value: 123, enumerable: true },
    p2: { value: 'abc', enumerable: true },
    p3: { get: function () { return this.p1 + this.p2 },
      enumerable:true,
      configurable:true
    }
  });
  
  // 判断自身的某个属性是否可遍历
  obj.propertyIsEnumerable('p') // true
  
  // 设置存取器
  const obj4 = {
    get p() {
      return 'getter';
    },
    set p(value) {
      console.log('setter: ' + value);
    }
  };
  
  // 使得一个对象无法添加新属性、无法删除旧属性、也无法改变属性的值。
  // 但是可以通过改变原型或者属性为对象的值改变对象
  Object.freeze(obj);
  Object.isFrozen(obj) // true
  
  ```

### Array

- `Array`构造函数不同的参数会导致行为不一致。单个正整数参数，表示返回的新数组的长度，用空值填充；单个非数值作为参数，则该参数是返回的新数组的成员；多参数时，所有参数都是返回的新数组的成员。

- ```js
  const arr = [1, 2, 3];
    
  Array.isArray(arr) // true
    
  arr.push(4, 5);
  arr // [1, 2, 3, 4, 5]
    
  arr.pop() // 3
  arr // [1, 2]
    
  arr.shift // 1
  arr // [2, 3]
    
  arr.unshift(0) // 4
  arr // [0, 1, 2, 3]
    
  arr.join('-') // '1-2-3'
  arr.join() // '1,2,3'
    
  // 不改变原数组，如果数组中包括对象，返回浅拷贝
  arr.concat([4, 5]) // [1, 2, 3, 4, 5]
  arr.concat(4, 5) // [1, 2, 3, 4, 5]
    
  arr.reverse() // [3, 2, 1]
    
  // 不改变原数组
  arr.slice(0,2) // [1, 2]
  arr.slice(-1) // [3]
    
  // 删除数组的一部分成员，并可以在删除的位置添加新的数组成员，返回被删除的元素，会改变原数组。
  // 第一个参数是删除的起始位置，第二个参数是被删除的元素个数，后面的参数为新插入的元素。
  arr.splice(0, 2, 5) // [1, 2]
  arr // [5, 3]
  arr.splice(-1, 1) // [3]
    
  // 默认按照字典顺序排序
  [11, 101].sort() // [101, 11]
  [11, 101].sort((a, b) => a - b) // [11, 101]
  
  // 返回给定元素在数组中第一次出现的位置，如果没有出现则返回-1, 可以指定第二个参数表示搜索的起始位置
  arr.indexOf(1) // 0
  arr.indexOf(1, 1) // -1
  
  // 判断数组整体是否满足某个条件
  arr.some(function (item, index, arr) {
    return item >= 2;
  }); // true
  arr.every(function (item, index, arr) {
    return elem >= 2;
  }); // false
  // 以下遍历方法不改变原数组
      
    // 返回新数组，可用第二个参数指定回调函数内的 this 指向
    arr.map((item, index, arr) => {
      return ...
    })
      
    // 无返回值
    arr.forEach((item, index, arr) => {
      ...
    })
  
    // 过滤数组成员，返回判断结果为 true 新数组
    arr.filter((item, index, arr) => {
      return ...
    })
  
    // 依次处理数组的每个成员，最终累计为一个值。第一个参数为一个函数，第二个参数为初始值。函数内第一个参数为上一次调用函数的返回值，若指定初始值则为初始值，第二个参数为当前变量
    arr.reduce((prev, cur, index, arr) => {
      return ...
    }, init)
  ```

### Number

- ```js
  Number.MAX_VALUE // 1.7976931348623157e+308
  Number.MAX_VALUE < Infinity // true
  
  Number.MIN_VALUE // 5e-324
  Number.MIN_VALUE > 0 // true
  
  // 能够精确表示的最大/小整数
  Number.MAX_SAFE_INTEGER // 9007199254740991
  Number.MIN_SAFE_INTEGER // -9007199254740991
  ```

- ```js
  // 可指定返回字符串的进制
  (10).toString() // "10"
  (10).toString(2) // "1010"
  
  // 先将一个数转为指定位数的小数，然后返回对应的字符串，小数5四舍五入不确定
  (10).toFixed(2) // "10.00"
  (10.005).toFixed(2) // "10.01"
  
  // 转为科学计数法
  (1234).toExponential()  // "1.234e+3"
  (1234).toExponential(1) // "1.2e+3"
  
  ```

### String

- ```js
  // 返回 Unicode 码点组成的字符串。
  String.fromCharCode(104, 101, 108, 108, 111) // "hello"
  ```

- ```js
  const str = 'hello world';
  
  str.length // 11
  
  str.charAt(0) // 'h'
  
  str.charCodeAt(0) // 104
  
  str.concat('!') // 'hello world!'
  str.concat('!', '!') // "hello world!!"
  
  str.slice(0, 5) // 'hello'
  str.slice(6) // 'world'
  str.slice(-5) // 'world'
  
  // 第一个参数是开始位置，第二个参数是长度
  str.substr(0, 5) // 'hello'
  
  //确定一个字符串在另一个字符串中第一次出现的位置，第二个参数表示开始搜索的位置
  str.indexOf('h') // 0
  str.indexOf('h', 2) // -1
  
  //去除首尾的空格，制表符，换行符等
  '  hello world '.trim() // 'hello world'
  
  'Hello World'.toLowerCase() // "hello world"
  'Hello World'.toUpperCase() // "HELLO WORLD"
  
  'cat, bat, sat, fat'.search('at') // 1
  
  'aaa'.replace('a', 'b') // "baa"
  
  // 返回由指定分割符分割出来的数组
  'a|b|c'.split('|') // ["a", "b", "c"]
  'a|b|c'.split('') // ["a", "|", "b", "|", "c"]
  'a|b|c'.split() // ["a|b|c"]
  ```

### Math

- ```js
  Math.E // 2.718281828459045
  Math.LN2 // 0.6931471805599453
  Math.LN10 // 2.302585092994046
  Math.LOG2E // 1.4426950408889634
  Math.LOG10E // 0.4342944819032518
  Math.PI // 3.141592653589793
  Math.SQRT1_2 // 0.7071067811865476
  Math.SQRT2 // 1.4142135623730951
  ```

- ```js
  Math.abs(-1) // 1
  
  Math.max(2, -1, 5) // 5
  Math.min(2, -1, 5) // -1
  
  Math.floor(3.2) // 3
  Math.floor(-3.2) // -4
  
  Math.ceil(3.2) // 4
  Math.ceil(-3.2) // -3
  
  Math.round(0.1) // 0
  Math.round(0.5) // 1
  Math.round(0.6) // 1
  Math.round(-1.1) // -1
  Math.round(-1.5) // -1
  Math.round(-1.6) // -2
  
  Math.pow(2, 3) // 8
  
  Math.sqrt(4) // 2
  
  // 在任意范围范围一个随机整数
  function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }
  
  ```

### Date

- 月份从`0`开始计算，天数从`1`开始计算。除了日期的默认值为`1`，小时、分钟、秒钟和毫秒的默认值都是`0`。
- `getTime()`：返回实例距离1970年1月1日00:00:00的毫秒数，等同于`valueOf`方法。
- `getDate()`：返回实例对象对应每个月的几号（从1开始）。
- `getDay()`：返回星期几，星期日为0，星期一为1，以此类推。
- `getFullYear()`：返回四位的年份。
- `getMonth()`：返回月份（0表示1月，11表示12月）。
- `getHours()`：返回小时（0-23）。
- `getMilliseconds()`：返回毫秒（0-999）。
- `getMinutes()`：返回分钟（0-59）。
- `getSeconds()`：返回秒（0-59）。

### RegExp

- ```js
  const regex = /xyz/i;
  const regex = new RegExp('xyz','i');
  ```

- 实例属性：

  - `RegExp.prototype.ignoreCase`：返回一个布尔值，表示是否设置了`i`修饰符。
  - `RegExp.prototype.global`：返回一个布尔值，表示是否设置了`g`修饰符。
  - `RegExp.prototype.multiline`：返回一个布尔值，表示是否设置了`m`修饰符。
  - `RegExp.prototype.flags`：返回一个字符串，包含了已经设置的所有修饰符，按字母排序。
  - `RegExp.prototype.lastIndex`：返回一个整数，表示下一次开始搜索的位置。该属性可读写，但是只在进行连续搜索时有意义。
  - `RegExp.prototype.source`：返回正则表达式的字符串形式（不包括反斜杠），该属性只读。

- ```js
  let r = /x/g;
  let s = '_x_x';
  
  r.lastIndex // 0
  r.test(s) // true
  r.lastIndex // 2
  r.test(s) // true
  r.lastIndex // 4
  r.test(s) // false
  
  let r = /a(b+)a/;
  let arr = r.exec('_abbba_aba_');
  
  arr // ["abbba", "bbb"]
  arr.index // 1
  arr.input // "_abbba_aba_"
  ```

- 字符串的实例方法：

  - `String.prototype.match()`：返回一个数组，成员是所有匹配的子字符串。如果正则表达式带有`g`修饰符，则该方法与正则对象的`exec`方法行为不同，会一次性返回所有匹配成功的结果。设置正则表达式的`lastIndex`属性，对`match`方法无效，匹配总是从字符串的第一个字符开始。
  - `String.prototype.search()`：按照给定的正则表达式进行搜索，返回一个整数，表示匹配开始的位置。如果没有任何匹配，则返回`-1`。
  - `String.prototype.replace()`：按照给定的正则表达式进行替换，返回替换后的字符串。它接受两个参数，第一个是正则表达式，表示搜索模式，第二个是替换的内容。正则表达式如果不加`g`修饰符，就替换第一个匹配成功的值，否则替换所有匹配成功的值。第二个参数还可以是一个函数，将每一个匹配内容替换为函数返回值。
  - `String.prototype.split()`：按照给定规则进行字符串分割，返回一个数组，包含分割后的各个成员。

- 匹配规则：

  - 字面量字符：`/dog/`表示`d`、`o`、`g`三个字母连在一起。

  - 元字符：

    - 点字符（`.`）匹配除回车、换行、行分隔符和段分隔符以外的所有字符：`c.t`匹配`c`和`t`之间包含任意一个字符的情况，比如`cat`、`c2t`、`c-t`等等，但是不匹配`coot`。

    - 位置字符：`^`表示字符串的开始位置，`$`表示字符串的结束位置

      ```js
      // test必须出现在开始位置
      /^test/.test('test123') // true
      
      // test必须出现在结束位置
      /test$/.test('new test') // true
      
      // 从开始位置到结束位置只有test
      /^test$/.test('test') // true
      /^test$/.test('test test') // false
      ```

    - 选择符（`|`）表示“或关系”，即`cat|dog`表示匹配`cat`或`dog`，选择符会包括它前后的多个字符。

  - 转义符：正则表达式中，需要反斜杠转义的，一共有12个字符：`^`、`.`、`[`、`$`、`(`、`)`、`|`、`*`、`+`、`?`、`{`和`\`。需要特别注意的是，如果使用`RegExp`方法生成正则对象，转义需要使用两个斜杠，因为字符串内部会先转义一次。
  - 特殊字符：
    - `\cX` 表示`Ctrl-[X]`，其中的`X`是A-Z之中任一个英文字母，用来匹配控制字符。
    - `[\b]` 匹配退格键(U+0008)，不要与`\b`混淆。
    - `\n` 匹配换行键。
    - `\r` 匹配回车键。
    - `\t` 匹配制表符 tab（U+0009）。
    - `\v` 匹配垂直制表符（U+000B）。
    - `\f` 匹配换页符（U+000C）。
    - `\0` 匹配`null`字符（U+0000）。
    - `\xhh` 匹配一个以两位十六进制数（`\x00`-`\xFF`）表示的字符。
    - `\uhhhh` 匹配一个以四位十六进制数（`\u0000`-`\uFFFF`）表示的 Unicode 字符。

  - 字符类：表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内，比如`[xyz]` 表示`x`、`y`、`z`之中任选一个匹配。如果方括号内的第一个字符是`[^]`，则表示除了字符类之中的字符，其他字符都可以匹配。比如，`[^xyz]`表示除了`x`、`y`、`z`之外都可以匹配。某些情况下，对于连续序列的字符，连字符（`-`）用来提供简写形式，表示字符的连续范围。比如，`[abc]`可以写成`[a-c]`，`[0123456789]`可以写成`[0-9]`，同理`[A-Z]`表示26个大写字母。
  - 预定义模式：
    - `\d` 匹配0-9之间的任一数字，相当于`[0-9]`。
    - `\D` 匹配所有0-9以外的字符，相当于`[^0-9]`。
    - `\w` 匹配任意的字母、数字和下划线，相当于`[A-Za-z0-9_]`。
    - `\W` 除所有字母、数字和下划线以外的字符，相当于`[^A-Za-z0-9_]`。
    - `\s` 匹配空格（包括换行符、制表符、空格符等），相等于`[ \t\r\n\v\f]`。
    - `\S` 匹配非空格的字符，相当于`[^ \t\r\n\v\f]`。
    - `\b` 匹配词的边界。
    - `\B` 匹配非词边界，即在词的内部。
  - 重复类：模式的精确匹配次数，使用大括号（`{}`）表示。`{n}`表示恰好重复`n`次，`{n,}`表示至少重复`n`次，`{n,m}`表示重复不少于`n`次，不多于`m`次。
  - 量词符：
    - `?` 问号表示某个模式出现0次或1次，等同于`{0, 1}`。
    - `*` 星号表示某个模式出现0次或多次，等同于`{0,}`。
    - `+` 加号表示某个模式出现1次或多次，等同于`{1,}`。
    - `+?`：表示某个模式出现1次或多次，匹配时采用非贪婪模式。
    - `*?`：表示某个模式出现0次或多次，匹配时采用非贪婪模式。
    - `??`：表格某个模式出现0次或1次，匹配时采用非贪婪模式。

  - 修饰符：
    - `g`修饰符表示全局匹配（global），加上它以后，正则对象将匹配全部符合条件的结果，主要用于搜索和替换。
    - `i`修饰符表示忽略大小写。
    - `m`修饰符表示多行模式（multiline），会修改`^`和`$`的行为。
  - 组匹配：括号表示分组匹配，括号中的模式可以用来匹配分组的内容。`(?:x)`称为非捕获组，表示不返回该组匹配的内容。`x(?=y)`称为先行断言，`x`只有在`y`前面才匹配，`y`不会被计入返回结果。`x(?!y)`称为先行否定断言，`x`只有不在`y`前面才匹配，`y`不会被计入返回结果。

### JSON 

- 每个 JSON 对象就是一个值，可能是一个数组或对象，也可能是一个原始类型的值。总之，只能是一个值，不能是两个或更多的值。
- JSON 对值的类型和格式有严格的规定：
  - 复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
  - 原始类型的值只有四种：字符串、数值（必须以十进制表示）、布尔值和`null`（不能使用`NaN`, `Infinity`, `-Infinity`和`undefined`）。
  - 字符串必须使用双引号表示，不能使用单引号。
  - 对象的键名必须放在双引号里面。
  - 数组或对象最后一个成员的后面，不能加逗号。
- `JSON`对象是 JavaScript 的原生对象，用来处理 JSON 格式数据。它有两个静态方法：`JSON.stringify()`和`JSON.parse()`。

