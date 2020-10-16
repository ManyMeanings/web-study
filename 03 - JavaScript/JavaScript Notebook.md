# JavaScript 笔记

-   JavaScript 是一种动态类型语言，使用`let`和`var`声明的变量可以随时重新赋值为其他类型的值。
-   标识符命名规则：
    -   第一个字符，可以是任意 Unicode 字母（包括中文），美元符号和下划线；
    -   后面的字符除了以上三种还可以是数字；
    -   不能为保留字。
-   对于`var`命令来说，JavaScript 的区块不构成单独的作用域。

    ## 数据类型

-   自动转为`false`的值：`undefined`，`null`，`false`，`0`，`NaN`，`""`（**注意：空数组，空对象和只有空格的字符串都自动转为`true`**）

-   JavaScript 内部，所有数字都是以 64 位浮点数形式储存，即使是整数也是如此。`1 === 1.0 // true`

-   全局方法`parseInt`规则：

    -   如果字符串头尾有空格，自动去除（`Number()`也是如此）；
    -   如果不是字符串，则先转为字符串再转换，从左至右遇到不能转为数字的字符时停止，如果最高位无法转换，返回`NaN`（不包括正负号接数字的情况）。

-   字符串是类数组，无法直接通过索引改变单个字符，也无法改变`length`属性。

-   对象的所有键名都是字符串（ES6 引入 Symbol 也可以作为键名），所以加不加引号都可以，如果键名是数值，会自动转为字符串。如果键名不是数值也不满足标识符的规则同时也没有加引号，会报错。

-   ```js
    const obj = {
    	name: 'Rick',
    	age: 21,
    };
    // 删除对象本身的属性
    delete obj.age; // true

    // 属性是否存在（包括继承的属性）
    'name' in obj; // true
    ```

-   ```js
    const fn = function (a, b) {
    	return a + b;
    };
    fn.name; // 'fn'

    // 定义时函数的参数个数
    fn.length; // 2
    ```

-   函数的作用域就是其声明时所在的作用域，与运行时的作用域无关。

-   `arguments`对象是一个类数组，包含函数运行时的所有对象，可读可写，但是在严格模式下与实际函数参数不具有联动关系。

-   闭包就是能够读取其他函数内部变量的函数，可以简单理解成定义在一个函数内部的函数。闭包除了能在函数外读取函数内部的变量以及封装私有属性和方法，还可以让这些变量始终保持在内存中，记住上一次调用时的运算结果。

-   立即执行函数的好处：避免污染全局变量。

-   清空数组的一个有效方法就是将`length`设为 0。

## 运算符

-   数值运算符（+）可以将任何值转为数值，与`Number()`的作用相同。

-   ```js
    1 === 0x1 // true
    NaN === NaN  // false
    +0 === -0 // true
    {} === {} // false
    ```

-   逗号运算符用于对两个表达式求值，并返回后一个表达式的值，主要用于在返回一个值之前进行一些辅助操作。

-   赋值运算符（`=`），三元条件运算符（`?:`）和指数运算符（`**`）是右结合运算符。

-   ```js
    // 布尔值：true 转成 1，false 转成 0
    Number(true); // 1
    Number(false); // 0

    // 转为0的情况
    Number(''); // 0
    Number(null); // 0

    // 转为 NaN 的情况
    Number('324abc'); // NaN
    Number(undefined); // NaN
    Number({ a: 1 }); // NaN
    ```

## 标准库

### Object

-   如果参数是原始类型的值，`Object`方法将其转为对应的包装对象的实例；如果参数是一个对象，它总是返回该对象，与`Object`构造函数基本相同，只是语意不同。

-   ```js
    var a = {};
    var b = { x: 1 };
    Object.setPrototypeOf(a, b);
    Object.getPrototypeOf(a) === b; // true
    a.x; // 1

    var o1 = {};
    var o2 = Object.create(o1);
    var o3 = Object.create(o2);
    o2.isPrototypeOf(o3); // true
    o1.isPrototypeOf(o3); // true

    function copyObject(orig) {
    	return Object.create(
    		Object.getPrototypeOf(orig),
    		Object.getOwnPropertyDescriptors(orig)
    	);
    }
    ```

-   ```js
    const obj = {
    	p1: 123,
    	p2: 'word',
    };

    // 遍历对象的属性，第二种方法还会返回不可枚举的属性名
    Object.keys(obj); // ["p1", "p2"]
    Object.getOwnPropertyNames(obj); // ["p1", "p2"]

    // 返回对象的值，自动类型转换会调用这个方法，默认返回对象本身
    obj === obj.valueOf(); // true
    //判断对象是否具有某个属性
    obj.hasOwnProperty('p1'); // true
    ```

-   每个对象的属性都有自己对应的属性描述对象，保存该属性的一些元信息：

    -   `value`：属性值
    -   `writable`：是否可写
    -   `enumerable`：是否可遍历
    -   `configurable`：属性描述对象的可写性
    -   `get`：该属性的取值函数
    -   `set`：该属性的存值函数

-   ```js
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
    	configurable: false,
    });
    const obj3 = Object.defineProperties(
    	{},
    	{
    		p1: { value: 123, enumerable: true },
    		p2: { value: 'abc', enumerable: true },
    		p3: {
    			get: function () {
    				return this.p1 + this.p2;
    			},
    			enumerable: true,
    			configurable: true,
    		},
    	}
    );

    // 判断自身的某个属性是否可遍历
    obj.propertyIsEnumerable('p'); // true

    // 设置存取器
    const obj4 = {
    	get p() {
    		return 'getter';
    	},
    	set p(value) {
    		console.log('setter: ' + value);
    	},
    };

    // 使得一个对象无法添加新属性、无法删除旧属性、也无法改变属性的值。
    // 但是可以通过改变原型或者属性为对象的值改变对象
    Object.freeze(obj);
    Object.isFrozen(obj); // true
    ```

### Array

-   `Array`构造函数不同的参数会导致行为不一致。单个正整数参数，表示返回的新数组的长度，用空值填充；单个非数值作为参数，则该参数是返回的新数组的成员；多参数时，所有参数都是返回的新数组的成员。

-   ```js
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

-   ```js
    Number.MAX_VALUE; // 1.7976931348623157e+308
    Number.MAX_VALUE < Infinity; // true

    Number.MIN_VALUE; // 5e-324
    Number.MIN_VALUE > 0; // true

    // 能够精确表示的最大/小整数
    Number.MAX_SAFE_INTEGER; // 9007199254740991
    Number.MIN_SAFE_INTEGER; // -9007199254740991
    ```

-   ```js
    // 可指定返回字符串的进制
    (10)
    	.toString()(
    		// "10"
    		10
    	)
    	.toString(2)
    	(
    		// "1010"

    		// 先将一个数转为指定位数的小数，然后返回对应的字符串，小数5四舍五入不确定
    		10
    	)
    	.toFixed(2)(
    		// "10.00"
    		10.005
    	)
    	.toFixed(2)
    	(
    		// "10.01"

    		// 转为科学计数法
    		1234
    	)
    	.toExponential()(
    		// "1.234e+3"
    		1234
    	)
    	.toExponential(1); // "1.2e+3"
    ```

### String

-   ```js
    // 返回 Unicode 码点组成的字符串。
    String.fromCharCode(104, 101, 108, 108, 111); // "hello"
    ```

-   ```js
    const str = 'hello world';

    str.length; // 11

    str.charAt(0); // 'h'

    str.charCodeAt(0); // 104

    str.concat('!'); // 'hello world!'
    str.concat('!', '!'); // "hello world!!"

    str.slice(0, 5); // 'hello'
    str.slice(6); // 'world'
    str.slice(-5); // 'world'

    // 第一个参数是开始位置，第二个参数是长度
    str.substr(0, 5); // 'hello'

    //确定一个字符串在另一个字符串中第一次出现的位置，第二个参数表示开始搜索的位置
    str.indexOf('h'); // 0
    str.indexOf('h', 2); // -1

    //去除首尾的空格，制表符，换行符等
    '  hello world '.trim(); // 'hello world'

    'Hello World'.toLowerCase(); // "hello world"
    'Hello World'.toUpperCase(); // "HELLO WORLD"

    'cat, bat, sat, fat'.search('at'); // 1

    'aaa'.replace('a', 'b'); // "baa"

    // 返回由指定分割符分割出来的数组
    'a|b|c'.split('|'); // ["a", "b", "c"]
    'a|b|c'.split(''); // ["a", "|", "b", "|", "c"]
    'a|b|c'.split(); // ["a|b|c"]
    ```

### Math

-   ```js
    Math.E; // 2.718281828459045
    Math.LN2; // 0.6931471805599453
    Math.LN10; // 2.302585092994046
    Math.LOG2E; // 1.4426950408889634
    Math.LOG10E; // 0.4342944819032518
    Math.PI; // 3.141592653589793
    Math.SQRT1_2; // 0.7071067811865476
    Math.SQRT2; // 1.4142135623730951
    ```

-   ```js
    Math.abs(-1); // 1

    Math.max(2, -1, 5); // 5
    Math.min(2, -1, 5); // -1

    Math.floor(3.2); // 3
    Math.floor(-3.2); // -4

    Math.ceil(3.2); // 4
    Math.ceil(-3.2); // -3

    Math.round(0.1); // 0
    Math.round(0.5); // 1
    Math.round(0.6); // 1
    Math.round(-1.1); // -1
    Math.round(-1.5); // -1
    Math.round(-1.6); // -2

    Math.pow(2, 3); // 8

    Math.sqrt(4); // 2

    // 在任意范围范围一个随机整数
    function getRandomInt(min, max) {
    	return Math.floor(Math.random() * (max - min + 1)) + min;
    }
    ```

### Date

-   月份从`0`开始计算，天数从`1`开始计算。除了日期的默认值为`1`，小时、分钟、秒钟和毫秒的默认值都是`0`。
-   `getTime()`：返回实例距离 1970 年 1 月 1 日 00:00:00 的毫秒数，等同于`valueOf`方法。
-   `getDate()`：返回实例对象对应每个月的几号（从 1 开始）。
-   `getDay()`：返回星期几，星期日为 0，星期一为 1，以此类推。
-   `getFullYear()`：返回四位的年份。
-   `getMonth()`：返回月份（0 表示 1 月，11 表示 12 月）。
-   `getHours()`：返回小时（0-23）。
-   `getMilliseconds()`：返回毫秒（0-999）。
-   `getMinutes()`：返回分钟（0-59）。
-   `getSeconds()`：返回秒（0-59）。

### RegExp

-   ```js
    const regex = /xyz/i;
    const regex = new RegExp('xyz', 'i');
    ```

-   实例属性：

    -   `RegExp.prototype.ignoreCase`：返回一个布尔值，表示是否设置了`i`修饰符。
    -   `RegExp.prototype.global`：返回一个布尔值，表示是否设置了`g`修饰符。
    -   `RegExp.prototype.multiline`：返回一个布尔值，表示是否设置了`m`修饰符。
    -   `RegExp.prototype.flags`：返回一个字符串，包含了已经设置的所有修饰符，按字母排序。
    -   `RegExp.prototype.lastIndex`：返回一个整数，表示下一次开始搜索的位置。该属性可读写，但是只在进行连续搜索时有意义。
    -   `RegExp.prototype.source`：返回正则表达式的字符串形式（不包括反斜杠），该属性只读。

-   ```js
    let r = /x/g;
    let s = '_x_x';

    r.lastIndex; // 0
    r.test(s); // true
    r.lastIndex; // 2
    r.test(s); // true
    r.lastIndex; // 4
    r.test(s); // false

    let r = /a(b+)a/;
    let arr = r.exec('_abbba_aba_');

    arr; // ["abbba", "bbb"]
    arr.index; // 1
    arr.input; // "_abbba_aba_"
    ```

-   字符串的实例方法：

    -   `String.prototype.match()`：返回一个数组，成员是所有匹配的子字符串。如果正则表达式带有`g`修饰符，则该方法与正则对象的`exec`方法行为不同，会一次性返回所有匹配成功的结果。设置正则表达式的`lastIndex`属性，对`match`方法无效，匹配总是从字符串的第一个字符开始。
    -   `String.prototype.search()`：按照给定的正则表达式进行搜索，返回一个整数，表示匹配开始的位置。如果没有任何匹配，则返回`-1`。
    -   `String.prototype.replace()`：按照给定的正则表达式进行替换，返回替换后的字符串。它接受两个参数，第一个是正则表达式，表示搜索模式，第二个是替换的内容。正则表达式如果不加`g`修饰符，就替换第一个匹配成功的值，否则替换所有匹配成功的值。第二个参数还可以是一个函数，将每一个匹配内容替换为函数返回值。
    -   `String.prototype.split()`：按照给定规则进行字符串分割，返回一个数组，包含分割后的各个成员。

-   匹配规则：

    -   字面量字符：`/dog/`表示`d`、`o`、`g`三个字母连在一起。

    -   元字符：

        -   点字符（`.`）匹配除回车、换行、行分隔符和段分隔符以外的所有字符：`c.t`匹配`c`和`t`之间包含任意一个字符的情况，比如`cat`、`c2t`、`c-t`等等，但是不匹配`coot`。

        -   位置字符：`^`表示字符串的开始位置，`$`表示字符串的结束位置

            ```js
            // test必须出现在开始位置
            /^test/.test('test123') // true

            // test必须出现在结束位置
            /test$/.test('new test') // true

            // 从开始位置到结束位置只有test
            /^test$/.test('test') // true
            /^test$/.test('test test') // false
            ```

        -   选择符（`|`）表示“或关系”，即`cat|dog`表示匹配`cat`或`dog`，选择符会包括它前后的多个字符。

    -   转义符：正则表达式中，需要反斜杠转义的，一共有 12 个字符：`^`、`.`、`[`、`$`、`(`、`)`、`|`、`*`、`+`、`?`、`{`和`\`。需要特别注意的是，如果使用`RegExp`方法生成正则对象，转义需要使用两个斜杠，因为字符串内部会先转义一次。
    -   特殊字符：

        -   `\cX` 表示`Ctrl-[X]`，其中的`X`是 A-Z 之中任一个英文字母，用来匹配控制字符。
        -   `[\b]` 匹配退格键(U+0008)，不要与`\b`混淆。
        -   `\n` 匹配换行键。
        -   `\r` 匹配回车键。
        -   `\t` 匹配制表符 tab（U+0009）。
        -   `\v` 匹配垂直制表符（U+000B）。
        -   `\f` 匹配换页符（U+000C）。
        -   `\0` 匹配`null`字符（U+0000）。
        -   `\xhh` 匹配一个以两位十六进制数（`\x00`-`\xFF`）表示的字符。
        -   `\uhhhh` 匹配一个以四位十六进制数（`\u0000`-`\uFFFF`）表示的 Unicode 字符。

    -   字符类：表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内，比如`[xyz]` 表示`x`、`y`、`z`之中任选一个匹配。如果方括号内的第一个字符是`[^]`，则表示除了字符类之中的字符，其他字符都可以匹配。比如，`[^xyz]`表示除了`x`、`y`、`z`之外都可以匹配。某些情况下，对于连续序列的字符，连字符（`-`）用来提供简写形式，表示字符的连续范围。比如，`[abc]`可以写成`[a-c]`，`[0123456789]`可以写成`[0-9]`，同理`[A-Z]`表示 26 个大写字母。
    -   预定义模式：
        -   `\d` 匹配 0-9 之间的任一数字，相当于`[0-9]`。
        -   `\D` 匹配所有 0-9 以外的字符，相当于`[^0-9]`。
        -   `\w` 匹配任意的字母、数字和下划线，相当于`[A-Za-z0-9_]`。
        -   `\W` 除所有字母、数字和下划线以外的字符，相当于`[^A-Za-z0-9_]`。
        -   `\s` 匹配空格（包括换行符、制表符、空格符等），相等于`[ \t\r\n\v\f]`。
        -   `\S` 匹配非空格的字符，相当于`[^ \t\r\n\v\f]`。
        -   `\b` 匹配词的边界。
        -   `\B` 匹配非词边界，即在词的内部。
    -   重复类：模式的精确匹配次数，使用大括号（`{}`）表示。`{n}`表示恰好重复`n`次，`{n,}`表示至少重复`n`次，`{n,m}`表示重复不少于`n`次，不多于`m`次。
    -   量词符：

        -   `?` 问号表示某个模式出现 0 次或 1 次，等同于`{0, 1}`。
        -   `*` 星号表示某个模式出现 0 次或多次，等同于`{0,}`。
        -   `+` 加号表示某个模式出现 1 次或多次，等同于`{1,}`。
        -   `+?`：表示某个模式出现 1 次或多次，匹配时采用非贪婪模式。
        -   `*?`：表示某个模式出现 0 次或多次，匹配时采用非贪婪模式。
        -   `??`：表格某个模式出现 0 次或 1 次，匹配时采用非贪婪模式。

    -   修饰符：
        -   `g`修饰符表示全局匹配（global），加上它以后，正则对象将匹配全部符合条件的结果，主要用于搜索和替换。
        -   `i`修饰符表示忽略大小写。
        -   `m`修饰符表示多行模式（multiline），会修改`^`和`$`的行为。
    -   组匹配：括号表示分组匹配，括号中的模式可以用来匹配分组的内容。`(?:x)`称为非捕获组，表示不返回该组匹配的内容。`x(?=y)`称为先行断言，`x`只有在`y`前面才匹配，`y`不会被计入返回结果。`x(?!y)`称为先行否定断言，`x`只有不在`y`前面才匹配，`y`不会被计入返回结果。

### JSON

-   每个 JSON 对象就是一个值，可能是一个数组或对象，也可能是一个原始类型的值。总之，只能是一个值，不能是两个或更多的值。
-   JSON 对值的类型和格式有严格的规定：
    -   复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
    -   原始类型的值只有四种：字符串、数值（必须以十进制表示）、布尔值和`null`（不能使用`NaN`, `Infinity`, `-Infinity`和`undefined`）。
    -   字符串必须使用双引号表示，不能使用单引号。
    -   对象的键名必须放在双引号里面。
    -   数组或对象最后一个成员的后面，不能加逗号。
-   `JSON`对象是 JavaScript 的原生对象，用来处理 JSON 格式数据。它有两个静态方法：`JSON.stringify()`和`JSON.parse()`。

## 面向对象编程

-   面向对象编程将真实世界各种复杂的关系，抽象为一个个对象，然后由对象之间的分工与合作，完成对真实世界的模拟。每一个对象都是功能中心，具有明确分工，可以完成接受信息、处理数据、发出信息等任务。面向对象编程具有灵活、代码可复用、高度模块化等特点，容易维护和开发，更适合多人合作的大型软件项目。

-   `new`命令的原理：

    1. 创建一个空对象，作为将要返回的对象实例。
    2. 将这个空对象的原型，指向构造函数的`prototype`属性。
    3. 将这个空对象赋值给函数内部的`this`关键字。
    4. 开始执行构造函数内部的代码。如果构造函数内部有`return`语句，而且`return`后面跟着一个对象，`new`命令会返回`return`语句指定的对象；否则，就会不管`return`语句，返回`this`对象。

-   函数内部可以使用`new.target`属性。如果当前函数是`new`命令调用，`new.target`指向当前函数，否则为`undefined`。使用这个属性，可以判断函数调用的时候，是否使用`new`命令。
-   由于函数可以在不同的运行环境执行，所以需要有一种机制，能够在函数体内部获得当前的运行环境（context），所以，`this`就出现了。`this`就是函数运行时所在的对象。
-   如果`this`所在的方法不在对象的第一层，这时`this`只是指向当前一层的对象，而不会继承更上面的层。
-   绑定对象的方法：`call`、`apply`、`bind`。
-   JavaScript 规定，所有对象都有自己的原型对象。一方面，任何一个对象，都可以充当其他对象的原型；另一方面，由于原型对象也是对象，所以它也有自己的原型，因此，就会形成一个“原型链”。读取对象的某个属性时，JavaScript 引擎先寻找对象本身的属性，如果找不到，就到它的原型去找，如果还是找不到，就到原型的原型去找。如果直到最顶层的`Object.prototype`还是找不到，则返回`undefined`。
-   `prototype`对象有一个`constructor`属性，默认指向`prototype`对象所在的构造函数。`constructor`属性的作用是，可以得知某个实例对象，到底是哪一个构造函数产生的。修改原型对象时，一般要同时修改`constructor`属性的指向。

## 异步操作

-   事件循环：JavaScript 运行时，除了一个正在运行的主线程，引擎还提供一个任务队列，里面是各种需要当前程序处理的异步任务（根据异步任务的类型，存在多个任务队列）。主线程首先执行所有的同步任务，等到同步任务全部执行完，就会去看任务队列里面的异步任务。如果满足条件，那么异步任务就重新进入主线程开始执行，这时它就变成同步任务了。一旦任务队列清空，程序就结束执行。
-   异步操作的模式：
    -   回调函数
    -   事件监听
    -   发布/订阅
-   `setTimeout`和`setInterval`的运行机制，是将指定的代码移出本轮事件循环，等到下一轮事件循环，再检查是否到了指定时间。如果到了，就执行对应的代码；如果不到，就继续等待。所以没有办法保证，`setTimeout`和`setInterval`指定的任务，一定会按照预定时间执行。
-   `setTimeout(f, 0)`可以调整事件的发生顺序。
-   `Promise`中`resolve`函数的作用是将`Promise`实例的状态从“未完成”变为“成功”（即从`pending`变为`fulfilled`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去。`reject`函数的作用是，将`Promise`实例的状态从“未完成”变为“失败”（即从`pending`变为`rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

## DOM

-   Node 接口:

    -   Node.prototype.nodeType：返回一个整数值，表示节点的类型。（元素节点为 1，属性节点为 2，文本节点为 3）

    -   Node.prototype.nodeName：返回节点的名称。

    -   Node.prototype.nodeValue：返回一个字符串，表示当前节点本身的文本值，该属性可读写。

    -   Node.prototype.textContent：返回当前节点和它的所有后代节点的文本内容。该属性是可读写的，设置该属性的值，会用一个新的文本节点，替换所有原来的子节点，而且自动对 HTML 标签转义，适合用于用户提供的内容。

    -   Node.prototype.baseURI：返回一个字符串，表示当前网页的绝对路径。

    -   Node.prototype.nextSibling：返回紧跟在当前节点后面的第一个同级节点。如果当前节点后面没有同级节点，则返回`null`。可以用来遍历所有子节点。

    -   Node.prototype.previousSibling：返回当前节点前面的、距离最近的一个同级节点。如果当前节点前面没有同级节点，则返回`null`。

    -   Node.prototype.parentNode：返回当前节点的父节点。包括元素节点、文档节点和文档片段节点

    -   Node.prototype.parentElement：返回当前节点的父元素节点。

    -   Node.prototype.firstChild/Node.prototype.lastChild：返回当前元素的第一个/最后一个字节点。

    -   Node.prototype.childNodes：返回一个类似数组的对象（`NodeList`集合），成员包括当前节点的所有子节点。使用该属性可以遍历某个节点的所有子节点。`NodeList`对象是一个动态集合，一旦子节点发生变化，立刻会反映在返回结果之中。

    -   Node.prototype.isConnected：返回一个布尔值，表示当前节点是否在文档之中。

    -   Node.prototype.appendChild()：接受一个节点对象作为参数，将其作为最后一个子节点，插入当前节点，返回值就是插入文档的子节点。

    -   Node.prototype.hasChildNodes()：返回一个布尔值，表示当前节点是否有子节点。

    -   Node.prototype.cloneNode()：用于克隆一个节点，接受一个布尔值作为参数，表示是否同时克隆子节点，返回值是一个克隆出来的新节点。保留`id`，`name`等属性，不保留监听事件。

    -   Node.prototype.insertBefore()：用于将某个节点插入父节点内部的指定位置。

        ```js
        const insertedNode = parentNode.insertBefore(newNode, referenceNode);
        ```

    -   Node.prototype.removeChild()：接受一个子节点作为参数，用于从当前节点移除该子节点。返回值是移除的子节点。

    -   Node.prototype.replaceChild()：用于将一个新的节点替换当前节点的某一个子节点。

        ```js
        const replacedNode = parentNode.replaceChild(newChild, oldChild);
        ```

    -   Node.prototype.contains()：返回一个布尔值，表示参数节点是否满足以下三个条件之一：参数节点为当前节点；参数节点为当前节点的子节点；参数节点为当前节点的后代节点。

-   ParentNodes 接口：

    -   ParentNode.children：返回一个`HTMLCollection`实例，成员是当前节点的所有元素子节点。该属性只读。

    -   ParentNode.firstElementChild：返回当前节点的第一个元素子节点。
    -   ParentNode.lastElementChild：返回当前节点的最后一个元素子节点。
    -   ParentNode.childElementCount：返回一个整数，表示当前节点的所有元素子节点的数目。
    -   ParentNode.append()：为当前节点追加一个或多个子节点，位置是最后一个元素子节点的后面。
    -   ParentNode.prepend()：为当前节点追加一个或多个子节点，位置是第一个元素子节点的前面。

-   ChildNode 接口：

    -   ChildNode.remove()：从父节点移除当前节点。
    -   ChildNode.before()：用于在当前节点的前面，插入一个或多个同级节点。两者拥有相同的父节点。
    -   ChildNode.after()：用于在当前节点的后面，插入一个或多个同级节点，两者拥有相同的父节点。
    -   ChildNode.replaceWith()：使用参数节点，替换当前节点。

-   Document 节点

    -   document.activeElement：返回获得当前焦点（focus）的 DOM 元素。
    -   document.fullscreenElement：返回当前以全屏状态展示的 DOM 元素。

    -   document.title：返回当前文档的标题，可写。
    -   document.referrer：返回一个字符串，表示当前文档的访问者来自哪里。

    -   document.hidden：返回一个布尔值，表示当前页面是否可见。如果窗口最小化、浏览器切换了 Tab，都会导致导致页面不可见，使得`document.hidden`返回`true`。
    -   document.visibilityState：返回文档的可见状态。

        -   `visible`：页面可见。页面可能是部分可见，即不是焦点窗口，前面被其他窗口部分挡住了。
        -   `hidden`：页面不可见，有可能窗口最小化，或者浏览器切换到了另一个 Tab。
        -   `prerender`：页面处于正在渲染状态，对于用户来说，该页面不可见。
        -   `unloaded`：页面从内存里面卸载了。

    -   document.querySelector()，document.querySelectorAll()：接受一个 CSS 选择器作为参数，返回匹配该选择器的元素节点。不支持 CSS 伪元素的选择器。
    -   document.getElementsByTagName()
    -   document.getElementsByClassName()
    -   document.getElementsByName()
    -   document.getElementById()
    -   document.createElement()：参数为元素的标签名，生成元素节点，并返回该节点。

    -   document.createTextNode()：参数为文本节点的内容，生成文本节点，并返回该节点。
    -   document.createAttribute()：生成一个新的属性节点，并返回它。

    -   document.addEventListener()，document.removeEventListener()，document.dispatchEvent()

-   Element 节点

    -   Element.id：返回指定元素的`id`属性，该属性可读写。
    -   Element.draggable：返回一个布尔值，表示当前元素是否可拖动。该属性可读写。

    -   Element.title：用来读写当前元素的 HTML 属性`title`。
    -   Element.attributes：返回一个类似数组的对象，成员是当前元素节点的所有属性节点。

    -   Element.className：读写当前元素节点的`class`属性。
    -   Element.dataset：可以自定义`data-`属性，用来添加数据。

    -   Element.innerHTML：返回一个字符串，等同于该元素包含的所有 HTML 代码。
    -   Element.outerHTML：返回一个字符串，表示当前元素节点的所有 HTML 代码，包括该元素本身和所有子元素。

    -   Element.clientHeight，Element.clientWidth ：包含内容和`padding`部分，不包含滚动条，只对块级元素生效。
    -   Element.clientLeft，Element.clientTop：只包括边框的宽度。

    -   Element.scrollHeight，Element.scrollWidth：包括溢出容器、当前不可见的部分。包括`padding`，伪元素，但是不包括`border`、`margin`以及水平滚动条的高度。
    -   Element.scrollLeft，Element.scrollTop：滚动条滚动的像素数量。

    -   Element.offsetParent：返回最靠近当前元素的、并且 CSS 的`position`属性不等于`static`的上层元素。
    -   Element.offsetHeight，Element.offsetWidth：包括元素本身的高度、padding 和 border，以及滚动条的高度。

    -   Element.offsetLeft，Element.offsetTop：返回当前元素左上角相对于`Element.offsetParent`节点的水平位移/垂直位移
    -   Element.style：行内样式信息
    -   Element.firstElementChild，Element.lastElementChild

    -   Element.nextElementSibling，Element.previousElementSibling
