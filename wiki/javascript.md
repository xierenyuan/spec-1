# javascript 编码规范 【待修订】
> 参考百度FEF  规范 

 * [1 前言](#1-前言)                 
 * [2 代码风格](#2-代码风格)     
   - [2.1 文件](#21-文件)    
   - [2.2 结构](#22-结构)  
   - [2.3 命名规则](#23-命名规则)
   - [2.4 注释](#24-注释)
   - [2.2 结构](#22-结构)    
 * [3 语言特性](#3-语言特性)                  
   - [3.1 类型](#31-类型)               
   - [3.2 引用](#32-引用)                 
   - [3.3 对象](#33-对象)     
   - [3.4 解构](#34-解构)  
   - [3.5 字符串模板](#35-字符串模板)  
   - [3.6 函数](#36-函数)  
   - [3.7 箭头函数](#37-箭头函数)     
   - [3.8 构造器](#38-构造器)   
   - [3.9 模块](#39-模块)   
   - [3.10 对象](#310-对象)             
   - [3.11 集合](#311-集合)            
   - [3.12 集合](#312-异步)    
   
   
## 1 前言 
    本文档的目标是使 JavaScript 代码风格保持一致，容易被理解和被维护。主要针对ES6 规范。

## 2 代码风格

### 2.1 文件
   除vue 文件外,所有的js 文件的理应设为 .js 为后缀
   排除基于ECMAScript 扩展的语言（jsx TypeScript 等）

### 2.2 结构

- 2.2.1 缩进       
  使用soft tab（4个空格）  
  `4` 空格为一个缩进，换行后添加一层缩进。将起始和结束的 `` ` `` 符号单独放一行，有助于生成 HTML 时的标签对齐。
为避免破坏缩进的统一，当空行与空白字符敏感时，建议使用 `多个模板字符串` 或 `普通字符串` 进行连接运算，也可使用数组 `join` 生成字符串。    
  [强制] 使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。    
  [强制] switch 下的 case 和 default 必须增加一个缩进层级。         
  [建议] 用多行模板字符串时遵循缩进原则。当空行与空白字符敏感时，不使用多行模板字符串。
  示例：

  ```javascript 
    // good
    switch (variable) {

        case '1':
            // do...
            break;

        case '2':
            // do...
            break;

        default:
            // do...

    }

    // bad
    switch (variable) {

    case '1':
        // do...
        break;

    case '2':
        // do...
        break;

    default:
        // do...

    }
  ```   

- 2.2.2 空格       
  [强制] 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。     
  示例：

  ```javascript 
  let a = '';
  a++;

  a = b + c;
  ```   

- 2.2.3 换行    
  换行的地方，行末必须有','或者运算符；   
  以下几种情况不需要换行:
  - 下列关键字后：__else__, __catch__, __finally__ 
  - 代码块'{'前    
  以下几种情况需要换行:    
  - 代码块'{'后和'}'前    
  - 变量赋值后  
  示例：

  ```javascript 
  // bad  缩进以有问题
  let a={
      b:1
      ,c:2
      
  }; 

  // good 
  let a = {
	b: 1,
	c: 2
  };

  // bar 
  x = y
    ? 1 : 2;

  // good 
  x = y ? 1 : 2;
  x = y ?
    1 : 2;  

  // bar 
  let a, foo = 7, b,
    c, bar = 8;  

  // good 
  let a,
    foo = 7,
    b, c, bar = 8;

  // 不需要换行
  if (condition) {
    ...
  } else {
        ...
  }  
  ```          

- 2.2.4 语句

### 2.3 命名规则

- 2.3.1 项目命名    
   全部采用小写方式， 以下划线`_`分隔。   
   列: `vue_ionic`丶 `mkt_label`   
- 2.3.2 目录命名
   全部采用小写方式，以`.` 分隔  
   有复数结构时，要采用复数命名法。  
   列： `src`,`assets`,`services`,`hello.word`
- 2.3.3 js文件命名
   参考目录命令   
   具体有意义的文件时需要带具体的后缀 如`.config.js`,`.service.js`,`.controller.js`,`.spec.js`   
   列： `bootstrap.js`,`hello.config.js`,`router.config.js`,'user.service.js'
- 2.3.4 变量命名
  - [强制]标准采用驼峰式命名 （除了对象的属性外，主要是考虑到后端返回的数据）  

  ```
  let user = '';
  let userName = '';
  ```
  - [强制] 'ID'在变量名中全大写   
  ```
  let userID = '';

  ```
  - [强制] 'URL'在变量名中全大写  
  ```
  let imgURL = '';

  ```
  - [强制] 'Android'在变量名中大写第一个字母  
  ```
   let AndroidVersion = '';
  ```
  - [强制] 'iOS'在变量名中小写第一个，大写后两个字母
  ```
  let iOSVersion = '';
  ``` 
  -  [强制] 常量全大写，用下划线连接  
  ```
  let API_HOST = '';
  ```
  - [强制] Class 类 大写第一个字母 
  ```
  class UIConfig {

  }
  ```
  - [强制] jquery对象必须以'$'开头命名    
  ```
  let $el = $('#id');

  ```

- [建议] 服务一般 定义建议首字母大写

```javascript 
let UserService = new UserService();
```

- [建议] boolean 类型的变量使用 is 或 has 开头。  

```javascript 
let isReady = false;
let hasMoreCommands = false;
```

- 2.3.5 变量声明
   一个函数作用域中所有的变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明。 
- 2.3.6 函数/方法/类 命名
- [强制] 类的 方法 / 属性 使用 驼峰命名法

  示例：

  ```javascript 
  class UIConfig {
      init() {

      }
  }
  ```   
 - [强制] 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。   
 - 强制] 类的 方法 / 属性 使用 Camel命名法。 
 - 参数之间用`, `分隔，注意逗号后有一个空格。   
  ```javascript 
  class UIConfig {
      XMLParser() {

      }
      insertHTML(element, html) {

      }
  }

  let httpRequest = new HTTPRequest();
 ``` 

 - [强制] 类名 使用 名词。 
 ``` javascript 
 class Engine {

 }
 ``` 

 - [强制] 函数的 参数 使用 Camel命名法。

 ```javascript 
 function stringFormat(source) {
 }

 function hear(theBells) {
 }

 ``` 

 - [建议] 函数的 事件的使用 on 开始命名 
 
  ```javascript
	class Engine {
	    onSave(){

	    }
      }
  ```

- [建议] 服务类 方法 遵循  
  - `get` 获取单条
  - `getByID` 根据 xx 获取
  - `getList` 获取列表 
  - `exportXX` 下载 下载xx(exportUser) 
  - `getXX` 获取xx   
 
	``` javascript
	class EngineService {
	    onSave(){
		get(){

		}

		getList(){

		}

		getByID(){

		}

		exportUser(){

		}

		getAids(){

		}
	    }
	 }
	```

- [建议] 初始化 方法定义遵循 xxInit() 
```javascript
class EngineCtrl {
    onSave(){
        menuInit(){

        }

        gridInit(){

        }
     
    }
 }
```


### 2.4 注释

- 2.4.1  单行注释
    - [强制] 双斜线后，必须跟一个空格； 
    - [强制] 缩进与下一行代码保持一致；
    - 可位于一个代码行的末尾，与代码间隔一个空格。
    ```
    // 这是a的注释
    let a = '';
    let b = ''; // 这是 b
    ```
    
- 2.4.2  多行注释
    - 最少三行, '*'后跟一个空格 
    - 一般使用 多个单行替代
    建议在以下情况下使用：   
       -  难于理解的代码段 
       -  可能存在错误的代码段 
       -  浏览器特殊的HACK代码  
       -  业务逻辑强相关的代码  
   ```
   /*
    * xxx a
    */
   let a = '';
   ```    
- 2.4.3  文档化注释
   各类标签@param, @method等请参考[usejsdoc](http://usejsdoc.org/) && [JSDoc Guide](http://yuri4ever.github.io/jsdoc/)
    - [强制] 为了便于代码阅读和自文档化，以下内容必须包含以 /**...*/ 形式的块注释中。
    解释：  
       - 文件
       - namespace
       - 类 
       - 函数或方法 
       - 类属性   
       - 事件 
       - 全局变量 
       - 常量 
       - AMD 模块    
    - [强制] 文档注释前必须空一行。     
    - [建议] 自文档化的文档说明 what，而不是 how。  

  ```javascript
    /**
    * 
    * 啦啦啦
    * @class Demo
    */
    class Demo {
        constructor() {

        }

        /**
        * 
        * f  
        * @param {number} id  xx 
        * @param {string} text xx
        * @param {Object} cls  xx
        * 
        * @memberOf Demo
        */
        f(id, text, cls) {

        }
    }
  ```  

- 2.4.4  类型定义  
 
 - [强制] 对于基本类型 {string}, {number}, {boolean}，首字母必须小写。      

| --      | 类型定义          | 语法示例      | 解释                           | 
|---------- |-------------- |---------- |--------------------------------  |
    |String|{string}|-|
    |Number|{number}|-|
    |Boolean|{boolean}|-|
    |Object|{Object}|-|
    |Function|{Function}|-|
    |RegExp|{RegExp}|-|
    |Array|{Array}|-|
    |Date|{Date}|-|
    |单一类型集合|{Array.&lt;string&gt;} |string 类型的数组|
    |多类型|{(number｜boolean)}| 可能是 number 类型, 也可能是 boolean 类型|
    |允许为null|{?number}|可能是 number, 也可能是 null|
    |不允许为null|{!Object}|Object 类型, 但不是 null|
    |Function类型|{function(number, boolean)}|函数, 形参类型|
    |Function带返回值|{function(number, boolean):string}|函数, 形参, 返回值类型|
    |Promise|Promise.&lt;resolveType, rejectType&gt;|Promise，成功返回的数据类型，失败返回的错误类型|
    |参数可选|@param {string=} name|可选参数, =为类型后缀|
    |可变参数|@param {...number} args|变长参数,  ...为类型前缀|
    |任意类型|{*}|任意类型|
    |可选任意类型|@param {*=} name|可选参数，类型不限|
    |可变任意类型|@param {...*} args|变长参数，类型不限|

    
- 2.4.5  文件注释
   - [强制] 文件顶部必须包含文件注释，用 @file 标识文件说明。
   - [建议] 文件注释中可以用 @author 标识开发者信息。 

- 2.4.6  命名空间注释
   - [建议] 命名空间使用 @namespace 标识。
   ```javascript
   /**
    * @namespace
    */
    let util = {};
   ```

- 2.4.7  类注释
  - [强制] 类的属性或方法等成员信息不是 public 的，应使用 @protected 或 @private 标识可访问性。
  - [建议] 使用 @extends 标记类的继承信息。
  - [建议] 使用 @class 标记类或构造函数。

- 2.4.8  函数/方法注释   
  - [强制] 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。 
  - [强制] 参数和返回值注释必须包含类型信息，且不允许省略参数的说明。 
  - [建议] 当函数是内部函数，外部不可访问时，可以使用 @inner 标识。
  - [强制] 对 Object 中各项的描述， 必须使用 @param 标识 

  ```javascript 

    /**
    * 
    * 啦啦啦
    * @class Demo
    */
    class Demo {
        constructor() {

        }


        /**
        * 
        * xx
        * @param {Object} params  xx 
        * @param {string} params.id xx 
        * @param {string} params.text xx
        * 
        * @memberOf Demo
        */
        f(params) {

        }
    }
  ```
  - [建议] 重写父类方法时， 应当添加 @override 标识。如果重写的形参个数、类型、顺序和返回值类型均未发生变化，可省略 @param、@return，仅用 @override 标识，否则仍应作完整注释。    
  解释：  
  简而言之，当子类重写的方法能直接套用父类的方法注释时可省略对参数与返回值的注释。  
- 2.4.9  事件注释
    - [强制] 必须使用 @event 标识事件，事件参数的标识与方法描述的参数标识相同   

- 2.4.10 常量注释
  - [强制] 常量必须使用 @const 标记，并包含说明和类型信息。


## 3 语言特性

### 3.1 类型
  - 3.1.1 基本类型: 直接存取基本类型。
    - 字符串
    - 数值
    - 布尔类型 
    - null
    - undefined
  ``` javascript 
    const foo = 1;
    let bar = foo;

    bar = 9;

    console.log(foo, bar); // => 1, 9
  ```  
  - 3.1.2 复制类型: 通过引用的方式存取复杂类型。   
    - 对象
    - 数组
    - 函数
  ``` javascript 
    const foo = [1, 2];
    const bar = foo;

    bar[0] = 9;

    console.log(foo[0], bar[0]); // => 9, 9
  ```  

  ### 3.2 引用        
   -  对所有的引用使用 const ；不要使用 var。 
  ``` javascript   
     // bad
    var a = 1;
    var b = 2;

    // good
    const a = 1;
    const b = 2;
   ``` 

   - 如果你一定需要可变动的引用，使用 let 代替 var。  
   ```javascript
     // bad
    var count = 1;
    if (true) {
        count += 1;
    }

    // good, use the let.
    let count = 1;
    if (true) {
        count += 1;
    } 
   ```

  - 注意 let 和 const 都是块级作用域。
  ```javascript
    // const 和 let 只存在于它们被定义的区块内。
    {
    let a = 1;
    const b = 1;
    }
    console.log(a); // ReferenceError
    console.log(b); // ReferenceError
   ```

### 3.3 对象

 - 使用字面值创建对象
```javascript
// bad
const item = new Object();

// good
const item = {};
```

 - 如果你的代码在浏览器环境下执行，别使用 保留字 作为键值。这样的话在 IE8 不会运行。 更多信息。 但在 ES6 模块和服务器端中使用没有问题。   
```javascript
// bad
const superman = {
  default: { clark: 'kent' },
  private: true,
};

// good
const superman = {
  defaults: { clark: 'kent' },
  hidden: true,
};
```

- 使用同义词替换需要使用的保留字。
```javascript
// bad
const superman = {
  class: 'alien',
};

// bad
const superman = {
  klass: 'alien',
};

// good
const superman = {
  type: 'alien',
};
```

- 创建有动态属性名的对象时，使用可被计算的属性名称。
```javascript
  function getKey(k) {
    return `a key named ${k}`;
  }

  // bad
  const obj = {
    id: 5,
    name: 'San Francisco',
  };
  obj[getKey('enabled')] = true;

  // good
  const obj = {
    id: 5,
    name: 'San Francisco',
    [getKey('enabled')]: true,
  };
```

- 使用对象方法的简写。
```javascript
 // bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

-  使用对象属性值的简写。
```javascript
 const lukeSkywalker = 'Luke Skywalker';

  // bad
  const obj = {
    lukeSkywalker: lukeSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
  };
```

- 在对象属性声明前把简写的属性分组。
``` javascript
  const anakinSkywalker = 'Anakin Skywalker';
  const lukeSkywalker = 'Luke Skywalker';

  // bad
  const obj = {
    episodeOne: 1,
    twoJedisWalkIntoACantina: 2,
    lukeSkywalker,
    episodeThree: 3,
    mayTheFourth: 4,
    anakinSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
    anakinSkywalker,
    episodeOne: 1,
    twoJedisWalkIntoACantina: 2,
    episodeThree: 3,
    mayTheFourth: 4,
  };
```

- 使用字面值创建数组。 
``` javascript
// bad
const items = new Array();

// good
const items = [];
```

- 向数组添加元素时使用 Arrary#push 替代直接赋值 
``` javascript
const someStack = [];


// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```

- 使用拓展运算符 ... 复制数组。
``` javascript
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

- 使用 Array#from 把一个类数组对象转换成数组。 
``` javascript
const foo = document.querySelectorAll('.foo');
const nodes = Array.from(foo);
```

### 3.4 解构  
- [强制] 不要使用3层及以上的解构。      
>  过多层次的解构会让代码变得难以阅读。    
- 使用解构存取和使用多属性对象。       
>  因为解构能减少临时引用属性。     

``` javascript
  // bad
  function getFullName(user) {
    const firstName = user.firstName;
    const lastName = user.lastName;

    return `${firstName} ${lastName}`;
  }

  // good
  function getFullName(obj) {
    const { firstName, lastName } = obj;
    return `${firstName} ${lastName}`;
  }

  // best
  function getFullName({ firstName, lastName }) {
    return `${firstName} ${lastName}`;
  }
``` 

- [建议] 使用解构减少中间变量。 
>  常见场景如变量值交换，可能产生中间变量。这种场景推荐使用解构。  

``` javascript
  // good
 [x, y] = [y, x];

 // bad
 let temp = x;
 x = y;
 y = temp;
``` 

-  对数组使用解构赋值。

``` javascript
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
``` 

- 需要回传多个值时，使用对象解构，而不是数组解构。   
>  增加属性或者改变排序不会改变调用时的位置。  

``` javascript
 // bad
  function processInput(input) {
    // then a miracle occurs
    return [left, right, top, bottom];
  }

  // 调用时需要考虑回调数据的顺序。
  const [left, __, top] = processInput(input);

  // good
  function processInput(input) {
    // then a miracle occurs
    return { left, right, top, bottom };
  }

  // 调用时只选择需要的数据
  const { left, right } = processInput(input);
``` 

- [强制] 仅定义一个变量时不允许使用解构。  
>  在这种场景下，使用解构将降低代码可读性。 

``` javascript
 // good
let len = myString.length;

// bad
let {length: len} = myString;
``` 

- [强制] 如果不节省编写时产生的中间变量，解构表达式 = 号右边不允许是 ObjectLiteral 和 ArrayLiteral。      
>   在这种场景下，使用解构将降低代码可读性，通常也并无收益。 
``` javascript
 // good
let {first: firstName, last: lastName} = person;
let one = 1;
let two = 2;

// bad
let [one, two] = [1, 2];
``` 

- [强制] 使用剩余运算符时，剩余运算符之前的所有元素必需具名。     
>   剩余运算符之前的元素省略名称可能带来较大的程序阅读障碍。如果仅仅为了取数组后几项，请使用 slice 方法。     
``` javascript
 // good
let [one, two, ...anyOther] = myArray;
let other = myArray.slice(3);

// bad
let [,,, ...other] = myArray;
``` 


### 3.5 字符串模板

- [强制] 字符串内变量替换时，不要使用 2 次及以上的函数调用。     
>  在变量替换符内有太多的函数调用等复杂语法会导致可读性下降。 
``` javascript
// good
let fullName = getFullName(getFirstName(), getLastName());
let s = `Hello ${fullName}`;

// bad
let s = `Hello ${getFullName(getFirstName(), getLastName())}`;
``` 
 


-  字符串使用单引号 ''  
``` javascript
 // bad
const name = "Capt. Janeway";

// good
const name = 'Capt. Janeway';
``` 

- 字符串超过 80 个字节应该使用字符串连接号换行。  

- 注：过度使用字串连接符号可能会对性能造成影响。jsPerf 和 讨论.  

```javascript   
// bad
const errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
const errorMessage = 'This is a super long error that was thrown because \
of Batman. When you stop to think about how Batman had anything to do \
with this, you would get nowhere \
fast.';

// good  这会不会用数组会更好一点
const errorMessage = 'This is a super long error that was thrown because ' +
  'of Batman. When you stop to think about how Batman had anything to do ' +
  'with this, you would get nowhere fast.';
```  

- 程序化生成字符串时，使用模板字符串代替字符串连接。    
>   模板字符串更为简洁，更具可读性。 
```javascript  
  // bad
  function sayHi(name) {
    return 'How are you, ' + name + '?';
  }

  // bad
  function sayHi(name) {
    return ['How are you, ', name, '?'].join();
  }

  // good
  function sayHi(name) {
    return `How are you, ${name}?`;
  }
```

### 3.6 函数

- [建议] 使用变量默认语法代替基于条件判断的默认值声明。  
>  添加默认值有助于引擎的优化，在未来 strong mode 下也会有更好的效果。  
```javascript  
// good
function foo(text = 'hello') {
}

// bad
function foo(text) {
    text = text || 'hello';
}
```

- [强制] 不要使用 arguments 对象，应使用 ...args 代替。  
>  使用 ... 能明确你要传入的参数。另外 rest 参数是一个真正的数组，而 arguments 是一个类数组。 

```javascript  
// good
function foo(...args) {
    console.log(args.join(''));
}

// bad
function foo() {
    console.log([].join.call(arguments));
}
```

- 使用函数声明代替函数表达式。          
>  函数声明是可命名的，所以他们在调用栈中更容易被识别。此外，函数声明会把整个函数提升（hoisted），而函数表达式只会把函数的引用变量名提升。这条规则使得箭头函数可以取代函数表达式。  

```javascript 
// bad
const foo = function () {
};

// good
function foo() {
} 
```

- 永远不要在一个非函数代码块（if、while 等）中声明一个函数，把那个函数赋给一个变量。浏览器允许你这么做，但它们的解析表现不一致。  

- 永远不要把参数命名为 arguments。这将取代原来函数作用域内的 arguments 对象。  
```javascript 
// bad
function nope(name, options, arguments) {
  // ...stuff...
}

// good
function yup(name, options, args) {
  // ...stuff...
} 
```

- 直接给函数参数赋值时需要避免副作用。  
>  这样的写法让人感到很困惑。
```javascript 
var b = 1;
// bad
function count(a = b++) {
  console.log(a);
}
count();  // 1
count();  // 2
count(3); // 3
count();  // 3 
```

### 3.7 箭头函数

-  当你必须使用函数表达式（或传递一个匿名函数）时，使用箭头函数符号。     
>   箭头函数创造了新的一个 this 执行环境（译注：参考 Arrow functions – JavaScript | MDN 和 ES6 arrow functions, syntax and lexical scoping），通常情况下都能满足你的需求，而且这样的写法更为简洁。
>  如果你有一个相当复杂的函数，你或许可以把逻辑部分转移到一个函数声明上。   

```javascript 
  // bad
  [1, 2, 3].map(function (x) {
    return x * x;
  });

  // good
  [1, 2, 3].map((x) => {
    return x * x;
  });
```

- 如果一个函数适合用一行写出并且只有一个参数，那就把花括号、圆括号和 return 都省略掉。如果不是，那就不要省略。   

```javascript
  // good
  [1, 2, 3].map(x => x * x);

  // good
  [1, 2, 3].reduce((total, n) => {
    return total + n;
  }, 0);
```
- [强制] 一个函数被设计为需要 `call` 和 `apply` 的时候，不能是箭头函数。  
>  箭头函数会强制绑定当前环境下的 this。


### 3.8 构造器

- 总是使用 `class`。避免直接操作 prototype 。  
>   `class` 语法更为简洁更易读。 

```javascript
  // bad
  function Queue(contents = []) {
    this._queue = [...contents];
  }
  Queue.prototype.pop = function() {
    const value = this._queue[0];
    this._queue.splice(0, 1);
    return value;
  }


  // good
  class Queue {
    constructor(contents = []) {
      this._queue = [...contents];
    }
    pop() {
      const value = this._queue[0];
      this._queue.splice(0, 1);
      return value;
    }
  }
```

- 使用 `extends` 继承。 
>  `extends` 是一个内建的原型继承方法并且不会破坏 `instanceof`。

```javascript  
  // bad
  const inherits = require('inherits');
  function PeekableQueue(contents) {
    Queue.apply(this, contents);
  }
  inherits(PeekableQueue, Queue);
  PeekableQueue.prototype.peek = function() {
    return this._queue[0];
  }

  // good
  class PeekableQueue extends Queue {
    peek() {
      return this._queue[0];
    }
  }
```

- 使用 super 访问父类成员，而非父类的 prototype。 
>  使用 super 和 super.foo 可以快速访问父类成员，而不必硬编码父类模块而导致修改和维护的不便，同时更节省代码。 

```javascript 
 // good
class TextNode extends Node {
    constructor(value, engine) {
        super(value);
        this.engine = engine;
    }

    setNodeValue(value) {
        super.setNodeValue(value);
        this.textContent = value;
    }
}

// bad
class TextNode extends Node {
    constructor(value, engine) {
        Node.apply(this, arguments);
        this.engine = engine;
    }

    setNodeValue(value) {
        Node.prototype.setNodeValue.call(this, value);
        this.textContent = value;
    }
}
```

- 方法可以返回 this 来帮助链式调用。

```javascript  
// bad
Jedi.prototype.jump = function() {
  this.jumping = true;
  return true;
};

Jedi.prototype.setHeight = function(height) {
  this.height = height;
};

const luke = new Jedi();
luke.jump(); // => true
luke.setHeight(20); // => undefined

// good
class Jedi {
  jump() {
    this.jumping = true;
    return this;
  }

  setHeight(height) {
    this.height = height;
    return this;
  }
}

const luke = new Jedi();

luke.jump()
  .setHeight(20);

```

### 3.9 模块

- export 与内容定义放在一起。  
>  何处声明要导出的东西，就在何处使用 export 关键字，不在声明后再统一导出。

```javascript 
// good
export function foo() {
}

export const bar = 3;


// bad
function foo() {
}

const bar = 3;

export {foo};
export {bar};
```

- 相互之间无关联的内容使用命名导出     
>   举个例子，工具对象中的各个方法，相互之间并没有强关联，通常外部会选择几个使用，则应该使用命名导出。
简而言之，当一个模块只扮演命名空间的作用时，使用命名导出。
-  所有 import 语句写在模块开始处
```javascript 
// good
import {bar} from './bar';

function foo() {
    bar.work();
}

// bad
function foo() {
    import {bar} from './bar';
    bar.work();
}
```

- 不要从 import 中直接 export   
>  虽然一行代码简洁明了，但让 import 和 export 各司其职让事情能保持一致。

```javascript  
  // bad
  // filename es6.js
  export { es6 as default } from './airbnbStyleGuide';

  // good
  // filename es6.js
  import { es6 } from './AirbnbStyleGuide';
  export default es6;
```

### 3.10 对象

- 定义对象时，如果所有键均指向同名变量，则所有键都使用缩写；如果有一个键无法指向同名变量，则所有键都不使用缩写。  
>  目的在于保持所有键值对声明的一致性。

```javascript  
 // good
let foo = {x, y, z};

let foo2 = {
    x: 1,
    y: 2,
    z: z
};


// bad
let foo = {
    x: x,
    y: y,
    z: z
};

let foo2 = {
    x: 1,
    y: 2,
    z
};
```

- 定义方法时使用 MethodDefinition 语法，不使用 PropertyName: FunctionExpression 语法。  
>  MethodDefinition 语法更清晰简洁。

```javascript  
 // good
let foo = {
    bar(x, y) {
        return x + y;
    }
};

// bad
let foo = {
    bar: function (x, y) {
        return x + y;
    }
};
```

- 使用 Object.keys 或 Object.entries 进行对象遍历   
> 不建议使用 for .. in 进行对象的遍历，以避免遗漏 hasOwnProperty 产生的错误。  

``` javascript 
// good
for (let key of Object.keys(foo)) {
    let value = foo[key];
}

// good
for (let [key, value] of Object.entries(foo)) {
    // ...
}
```

- 定义对象的方法不应使用箭头函数。  
>  箭头函数将 this 绑定到当前环境，在 obj.method() 调用时容易导致不期待的 this。除非明确需要绑定 this，否则不应使用箭头函数。  


``` javascript 
// good
let foo = {
    bar(x, y) {
        return x + y;
    }
};

// bad
let foo = {
    bar: (x, y) => x + y
};
```

- 尽量使用计算属性键在一个完整的字面量中完整地定义一个对象，避免对象定义后直接增加对象属性    
>  在一个完整的字面量中声明所有的键值，而不需要将代码分散开来，有助于提升代码可读性

``` javascript 
// good
const MY_KEY = 'bar';
let foo = {
    [MY_KEY + 'Hash']: 123
};

// bad
const MY_KEY = 'bar';
let foo = {};
foo[MY_KEY + 'Hash'] = 123;
```

### 3.11 集合

- 对数组进行连接操作时，使用数组展开语法  
>  用数组展开代替 concat 方法，数组展开对 Iterable 有更好的兼容性。

``` javascript 
// good
let foo = [...foo, newValue];
let bar = [...bar, ...newValues];

// bad
let foo = foo.concat(newValue);
let bar = bar.concat(newValues);
```

- 不要使用数组展开进行数组的复制操作。  
>  使用数组展开语法进行复制，代码可读性较差。推荐使用 Array.from 方法进行复制操作。

``` javascript 
// good
let otherArr = Array.from(arr);

// bad
let otherArr = [...arr];
```

- 需要一个不可重复的集合时，应使用 Set。     
>  不要使用 {foo: true} 这样的普通 Object。

```javascript   
// good
let members = new Set(['one', 'two', 'three']);

// bad
let members = {
    one: true,
    two: true,
    three: true
};
```

- 当需要遍历功能时，使用 Map 和 Set。   
>  Map 和 Set 是可遍历对象，能够方便地使用 for...of 遍历。不要使用使用普通 Object 
``` javascript  
// good
let membersAge = new Map([
    ['one', 10],
    ['two', 20],
    ['three', 30]
]);
for (let [key, value] of map) {
}

// bad
let membersAge = {
    one: 10,
    two: 20,
    three: 30
};
for (let key in membersAge) {
    if (membersAge.hasOwnProperty(key)) {
        let value = membersAge[key];
    }
}
```

- 程序运行过程中有添加或移除元素的操作时，使用 Map 和 Set。  
>  使用 Map 和 Set，程序的可理解性更好；普通 Object 的语义更倾向于表达固定的结构。

```javascript  
// good
let membersAge = new Map();
membersAge.set('one', 10);
membersAge.set('two', 20);
membersAge.set('three', 30);
membersAge.delete('one');

// bad
let membersAge = {};
membersAge.one = 10;
membersAge.two = 20;
membersAge.three = 30;
delete membersAge['one'];
```

### 3.12 异步  

- 回调函数的嵌套不得超过3层。   
>  深层次的回调函数的嵌套会让代码变得难以阅读。  

```javascript 
// bad
getUser(userId, function (user) {
    validateUser(user, function (isValid) {
        if (isValid) {
            saveReport(report, user, function () {
                notice('Saved!');
            });
        }
    });
});
```

- 使用 Promise 代替 callback   
>  相比 callback，使用 Promise 能够使复杂异步过程的代码更清晰

```javascript  
// good
let user;
getUser(userId)
    .then(function (userObj) {
        user = userObj;
        return validateUser(user);
    })
    .then(function (isValid) {
        if (isValid) {
            return saveReport(report, user);
        }

        return Promise.reject('Invalid!');
    })
    .then(
        function () {
            notice('Saved!');
        },
        function (message) {
            notice(message);
        }
    );
```

- 使用 async/await 代替 generator + co  【Koa 2】 
