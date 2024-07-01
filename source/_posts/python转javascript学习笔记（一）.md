---
title: python转javascript学习笔记（一）
top: false
cover: false
toc: true
mathjax: true
tags: 'javascript, python, 单线程, 异步'
date: 2024-06-18 12:39:30
password:
summary:
categories:
---

# JavaScript简介
## 语言规范
JavaScript语言遵循ECMAScript规范（简称ES），ECMA即欧洲计算机协会，该规范定义了JavaScript（以下统一使用js缩写）语言的核心特性，确保不同环境下的js实现（比如浏览器内置js引擎、Nodejs、其他服务器端js运行时等）的一致性和互操作性。ES6或ES2015（2015年6月发行）是该规范发行以来的一个重要里程碑，也是主流浏览器基本支持的版本。

## 特性和应用场景
1. 基于原型的面向对象语言，在动态修改和扩展对象上更加灵活（弱化了结构和可维护性）。
- 与传统的面向对象编程范式（Java/C++/C#等）的主要区别：
	- 创建机制：创建对象时，无需定义类模板，通过从对已有对象的克隆或引用创建；
	- 继承机制：直接从原型对象继承属性和方法，通过原型链实现；
	- 方法共享：所有继承自原型的对象共享同一个方法的引用，减少内存使用。

2. 动态弱类型语言
不需要显式声明对象类型（可使用var关键字），并且可在运行时修改对象类型（比如将一个对象从数字改成字符串），类型转换是隐式的。
- 动态vs静态：静态类型语言指代码在编译时检测变量类型，从而避免可能的类型错误，典型语言如C、C++、Java、C#；动态类型语言则是在运行时才检查变量的类型，意味着你可以随时改变变量的类型，代价是降低了程序的稳定性和安全性，代表性语言Python、Ruby、Javascript和PHP。
- 弱类型vs强类型：强类型语言中，变量的类型在定义和检查时都比较严格，一旦赋予类型，不支持隐式地类型转换（自动转换），如果要转换，必须显式转换，典型例子：Java、C# 和 Rust；弱类型语言中，类型检查较为宽松，可以进行变量类型自动转换（隐式转换），比如数字和字符串可以相互转换，或者布尔值可以转换为数字，典型例子：早期Javascript和Visual Basic。
	- 许多现代编程语言（如 TypeScript 或 Python 3）都在向更强类型的方向发展，即使它们传统上被认为是弱类型或动态类型的。这些语言通过引入类型注解、静态类型检查工具或其他机制来增强类型安全性，同时保持了一定程度的灵活性。


## 主要功能和应用
了解js语言的功能和用途有助于掌握js语言的能力边界，在实际解决问题的过程中更好地选用语言、框架、技术栈，提升开发效率、降低开发难度。
1. **web（前段）开发**
	- **动态网页**：JavaScript可以用来创建交互式的网页元素，如下拉菜单、弹出窗口、表单验证等。
	>为什么可以使用js实现交互式动态网页？
	>js运行在浏览器端，借助浏览器DOM操作实现对网页元素的访问和修改；通过事件处理机制实现对用户操作的监听和响应；通过AJAX异步请求等方式和服务器端进行通信，访问后端数据等。
	- **DOM操作**：JavaScript可以动态地修改HTML文档中的内容和样式，从而实现页面的实时更新。
	- **AJAX**：通过异步数据请求，JavaScript可以实现在不刷新整个页面的情况下更新部分内容，提升用户体验。
	- **框架和库**：如React、Angular和Vue.js等前端框架，它们基于JavaScript，用于构建复杂的Web应用程序。
2. **服务器端开发**：
    - **Node.js**：使开发者能够使用JavaScript进行服务器端编程，从而实现全栈JavaScript开发。
    - **数据库操作**：通过Node.js，JavaScript可以与各种数据库（如MongoDB、MySQL）进行交互，实现数据存储和检索。
3. **游戏开发**：
    - **Canvas API**：用于创建2D图形和动画，常用于浏览器游戏开发。
    - **WebGL**：用于3D图形渲染，使得复杂的游戏和可视化应用成为可能。
4. **移动应用开发**：
    - **React Native**、**Ionic**和**Cordova**等框架允许使用JavaScript开发跨平台的移动应用。
5. **桌面应用程序**：
    - **Electron**框架使得使用Web技术（HTML、CSS和JavaScript）开发跨平台的桌面应用程序成为可能。
6. **物联网（IoT）**：
    - **Node-RED**：一个基于Node.js的流媒体处理工具，用于构建物联网应用的数据流网络。
7. **数据可视化**：
    - **D3.js**等库可以帮助开发者从数据中创建复杂的可视化图表和图形。
7. **自动化任务**：
    - 使用Node.js，JavaScript可以编写自动化脚本来执行服务器管理、文件操作、构建过程等任务。
9. **机器学习**：
    - **TensorFlow.js**：允许在浏览器或Node.js环境中执行机器学习模型。

# 使用
## 开发工具
vscode（编辑器），Nodejs（解释运行），google浏览器开发者工具（自带js引擎，调试）
## 命名习惯
- 变量：驼峰命名法
- 常量：全大写，下划线间隔
- 函数：动词在前，驼峰命名法
- 文件名：全小写，下划线间隔
## 教程参考
- [JavaScript 基础 - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [Javascript 简介 - 白月黑羽 (byhy.net)](https://www.byhy.net/web/js/01/)


## 笔记
如果你和我一样平时使用python较多，那么以下知识点你可能需要关注一下。

### 变量

> let和var关键字区别
在JavaScript中，`let` 和 `var` 都用于声明变量，但它们之间有几个重要的区别：

1. **作用域**:
   - `var` 声明的变量具有函数作用域或全局作用域。这意味着在一个函数内部声明的变量在整个函数内部都是可见的，而在函数外部声明的变量则在整个脚本或全局范围内可见。
   - `let` 声明的变量具有块级作用域。这意味着变量仅在其被声明的代码块（由 `{}` 包围的区域，如循环或条件语句）内可见。

2. **变量提升 (Hoisting)**:
   - `var` 声明的变量会被提升至作用域的顶部，即在函数或全局作用域的最开始处声明，尽管实际声明可能出现在作用域内的任何位置。
   - `let` 声明的变量不会被提升。变量必须在使用之前声明，否则会抛出引用错误。

3. **重复声明**:
   - 使用 `var` 可以在同一作用域内多次声明同一个变量名，后一个声明会覆盖前一个。
   - 使用 `let` 在同一作用域内不允许重复声明同一个变量名，尝试这样做会导致语法错误。

4. **暂时性死区 (Temporal Dead Zone)**:
   - `var` 声明的变量在提升之后就可以访问，尽管访问时值为 `undefined`。
   - `let` 声明的变量在声明之前访问会抛出错误，这是因为变量存在于暂时性死区中直到其声明点。

5. **全局属性**:
   - 如果在全局作用域中使用 `var` 声明变量，该变量会自动成为全局对象（通常是 `window` 对象在浏览器环境中）的属性。
   - 使用 `let` 在全局作用域声明的变量不会成为全局对象的属性。

总结来说，`let` 提供了更严格的变量管理，增强了代码的可预测性和维护性。因此，现代JavaScript编码实践中通常推荐使用 `let` 而不是 `var`。同时，随着ES6的普及，`const` 也被广泛用于声明不可变的常量。

### 字符串 引号
js中的字符串可以用单引号、双引号、反引号，以下定义都可以：
```js
'字符串'
"字符串"
`字符串`
```
### 逻辑操作
松散相等比较和严格相等比较
- 严格相等比较：`1===1`返回true， `1==='1'`返回false
- 松散相等比较：`1=='1'`返回true，在比较时会尝试转化为同种类型进行比较
不相等同理。

### 对象
我们看到的js中通过字面量语法创建的对象和python中的字典类型在形式上有些相似，都是键值对的组合，比如：
```js
var student{
	name: '张三'，
	age: 23
}
```
并且js中的对象也支持通过`[]`访问对象的属性：`student['name']`，但两者在很多细节上存在一些关键区别：

1. **语法差异**:
   - 在JavaScript中，对象通常使用**字面量**语法定义，例如 `{key: value}` ，或通过构造函数 `new Object()` 创建。
   - 在Python中，字典使用花括号 `{}` 并且键值对之间用冒号 `:` 分隔。

2. **属性访问**:
   - JavaScript中，对象的属性可以通过点符号 `.` 或方括号 `[]` 访问，例如 `obj.key` 或 `obj['key']`（适合属性名中有空格等特殊字符、属性名为变量的情况）。
   - Python中，字典的元素只能通过方括号访问，例如 `dict['key']`。你不能使用点符号访问字典元素。

3. **动态属性**:
   - JavaScript对象允许动态添加属性，即可以在运行时向对象添加新的键值对。
   - Python字典同样支持动态添加键值对。

4. **原型继承**:
   JavaScript对象基于原型继承，这意味着一个对象可以从另一个对象继承属性和方法。这使得JavaScript对象具有层次结构和动态性。
   - Python字典没有这样的原型链概念，它们只包含自己的键值对，并不从其他字典继承任何东西。

5. **内置方法和功能**:
   - JavaScript对象和Python字典都有一系列内置的方法用于操作数据，但具体的方法可能不同。
   - 例如，JavaScript中的 `hasOwnProperty`, `keys`, `values`, 和 `entries` 方法，以及Python中的 `keys()`, `values()`, `items()`, 和 `get()` 方法等。

6. **用途和上下文**:
   - JavaScript对象常用于面向对象编程（OOP），并可以作为类的实例。
   - Python字典更常用作数据结构，用于存储和检索复杂的数据关联。

7. **性能和优化**:
   - JavaScript引擎通常会对对象的属性访问进行优化，例如V8引擎的内联缓存。
   - Python字典的性能取决于Python解释器的实现，如CPython，它使用哈希表来实现字典，这通常提供了快速的查找时间。

这些差异反映了两种语言的设计哲学和目标，JavaScript更多地被设计为一种用于Web的脚本语言，而Python则是一种通用的、高级的编程语言。
```ad-note
title: 哪些数据类型是对象？哪些不是对象？
- 对象是基于键值对的无序集合，其中的键（也称为属性名）是字符串，而值可以是任意数据类型，包括函数（作为方法）、其他对象、原始类型（如数字、字符串、布尔值）等。
	- 对象是属性和方法的集合，属性用于描述对象状态，方法是封装在对象中的函数，用于执行操作或算法。两者都可以通过`.`或`[]`访问，但调用方法需要加`()`。
	- ==函数本身也是一种对象，因为函数拥有name和desc属性==。
	- 
- 非对象：
	- **基本数据类型（Primitive Types）**：包括 `number`、`string`、`boolean`、`undefined` 和 `null`。这些类型不是对象，它们是不可变的值。
    
	- **Symbol**：ES6 引入的 Symbol 类型也不是对象，它用于创建唯一的键，常用于对象属性名。
```

```ad-note
title: 如何创建对象？
- **字面量形式创建的对象**：可以直接使用大括号 `{}` 来定义一个对象，其中可以包含各种属性和方法。
    
    ```js
    const obj = { key: 'value', method: function() { /* ... */ } };
    ```
    
- **通过构造函数创建的对象**：可以使用函数作为构造器，通过 `new` 关键字来创建对象实例。
    
    ```Javascript
    function Person(name) {
      this.name = name;
    }
    const person = new Person('Alice');
    ```
    
- **使用 `Object.create()` 方法**：可以指定一个原型对象，创建的新对象将继承原型对象的属性和方法。
 
    ```Javascript
    const prototype = { method: function() { /* ... */ } };
    const obj = Object.create(prototype);
    ```
    
- **类（Class）**：ES6 引入了类语法，提供了一种更清晰的方式来定义对象和继承。
    
    ```Javascript
    class Animal {
      constructor(name) {
        this.name = name;
      }
    }
    const animal = new Animal('Lion');
    ```
- **内置对象**：JavaScript 提供了许多内置对象，如 `Array`、`Date`、`Function`、`Math`、`String` 等，它们都是对象。
```


### 原型和原型链

原型和原型链理解js面向对象和继承机制的核心，是实现对象间属性和方法共享的基础。

每个JavaScript对象，除了`null`，都有一个内部属性`Prototype`，它引用了另一个对象。这个被引用的对象就是当前对象的原型。
JavaScript的继承机制是基于原型的，这意味着每个对象都有一个原型（除了`null`），并且可以通过原型链访问属性和方法。
#### 继承机制
- 原型继承

当试图访问一个对象的属性或方法时，如果该对象本身不包含所查找的属性或方法，JavaScript引擎会沿着原型链向上查找，直到找到该属性或方法，或者到达原型链的末端。

- 默认继承

即使你不显式地设置一个对象的原型，它也会自动继承自`Object.prototype`，这是所有对象共享的基本原型，包含了如`toString`、`valueOf`等基本方法。

```js
const obj = {};
console.log(obj.toString()); // "[object Object]"
```

在这个例子中，`obj`对象没有显式地设置原型，但它仍然可以调用`toString`方法，这是因为`toString`方法存在于`Object.prototype`上，`obj`隐式地继承了这个方法。

#### 原型链好处——属性和方法共享
原型属性是属于该原型链的所有对象共享的，节约了内存，避免了重复定义。
```ad-attention
即使先创建对象，再给其原型添加属性，已经创建的对象也具有后添加的属性。
```
### for循环
遍历对象时，除了可以使用`for...in...`语法，还有一种`for...of...`语法。
两者区别：
`for...of`循环用于遍历可迭代（Iterable）对象，如数组、字符串、Map、Set等。它按照元素的顺序访问每个元素的值，而不是键或索引。这对于需要访问集合中元素的实际值的场景非常有用。
```js
const fruits = ['apple', 'banana', 'cherry']; 
for (const fruit of fruits) { 
	console.log(fruit); 
	}
```
`for...in`循环则用于枚举一个对象的所有可枚举属性的键。这在遍历对象的属性时非常有用，但它返回的是属性名，而不是属性值。对于数组来说，它会遍历数组的索引，包括稀疏数组中的未定义项以及继承的属性。
```js
const person = { name: 'John', age: 30, city: 'New York' }; 
for (const prop in person) { 
	if (person.hasOwnProperty(prop)) { 
	console.log(`${prop}: ${person[prop]}`); 
	} 
}
```

### 剩余参数
剩余参数语法可以将一个不定数量的参数表示为一个数组，用`...`表示。相当于python中的可变参数列表`*args`
```js
var fruitInfo = {
	'apple' : 4,
	'banana': 10,
	'peach': 6,
	'watermelon': 3,
}

function printFruitInfo(...fruits){
	for(let fruit of fruits){
		console.log(`fruit: ${fruit}, num: ${fruitInfo[fruit]}`);
	}
}
//调用函数
printFruitInfo('apple', 'banana', 'peach')
```
上述代码使用python表示时：
```python
fruit_info = { 'apple': 4, 'banana': 10, 'peach': 6, 'watermelon': 3, } 
def print_fruit_info(*fruits): 
	for fruit in fruits: 
		print(f"fruit: {fruit}, num: {fruit_info[fruit]}") 
# 调用函数 
print_fruit_info('apple', 'banana', 'peach')
```

### 单线程异步编程
js最初设计被用于进行web开发，通过事件处理机制来对用户事件进行监听和响应，js引擎使用异步架构。
在js中，异步（Asynchronous）编程是一种允许你的程序在等待某些耗时操作（如网络请求、文件读写、定时器、数据库查询等）完成的同时，继续执行其他任务的编程模式。异步编程是JavaScript处理并发和I/O密集型操作的关键特性，它使得Web应用程序能够保持响应性和性能。

与之相对的是同步（Synchronous）编程，其中程序会按顺序执行每一行代码，如果遇到耗时操作，程序会停下来等待这个操作完成，然后再继续执行下一行代码。这在单线程环境中（如JavaScript在浏览器中的执行环境）会导致阻塞，降低用户体验，尤其是在处理长时间运行的任务时。

JavaScript使用事件循环（Event Loop）机制来支持异步编程。事件循环检查是否有待处理的事件或回调函数，如果有，就将它们加入到执行队列中，然后在当前任务完成后按顺序执行这些任务。这意味着，即使你的代码中包含了一些耗时操作，js引擎也不会停止执行其他代码，而是将这些耗时操作委托给操作系统或者其他线程去处理，一旦这些操作完成，再通过回调函数、Promise、async/await等方式通知主执行线程。

需要注意的是，js从设计之初就是一个单线程语言，即使看上去回调函数和主程序在并发执行，但其实都运行在一个主线程中。这种单线程异步编程方式的优点在于：
- 不需要考虑线程同步和资源竞争；
-  从源头上避免了线程间的切换，降低线程自身开销；

#### 常见的异步编程方式

1. **回调函数（Callback）**：将一个函数作为参数传递到另一个函数中，并在另一个函数中调用，这个函数就是回调函数（两个条件，外部调用，内部定义）。回调函数需要预先定义好，在发起异步操作时，同时提供一个回调函数，当异步操作完成时调用这个函数。
```js
//setTimeout模仿异步操作，两秒后调用回调函数callback
function fetchData(callback) { 
	setTimeout(() => { 
		const data = 'Hello from the server!'; 
		callback(data); 
		}, 2000); 
	}
fetchData((data) => { 
	console.log(data); 
	});
```
回调函数缺点：当需要依次执行多个异步操作时，容易陷入回调地狱。

2. **Promise**：一种更为现代的处理异步操作的方法，允许以**链式**调用的方式处理异步操作的结果，通过链式调用避免层层嵌套，提升可读性。js中的fetch API就是一个很好的例子。
```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
	.then((response)=>response.json())
	.then((json)=>{
		console.log(json);
	})
	.catch((error)=>{
		console.error(error);
	})
	finally(()=>{
		stopLoadingAnimation();              //类似try-catch-finally结构
	});

```
Promise是ES6中引入的用于简化异步编程的构造。Promise对象代表一个最终可能完成或失败的异步操作，它有三种状态：pending（等待中）、fulfilled（已完成）和rejected（已拒绝）。
从字面理解`Promise`——承诺会在未来某个时刻返回数据，异步函数可以理解为返回值为Promise对象的函数。

3. **Async/Await**：基于Promise的语法糖（不改变实际功能，但提升程序可读性），使异步代码看起来更像同步代码，提高了代码的可读性和可维护性。
```js
async function f(){  //使用async关键字将函数标记为异步函数
	const response = await fetch("http://") //使用await代替then 
	const json = await response.json();
	console.log(json);
}  
f(); 
```
异步编程虽然增加了代码的复杂性，但它是构建高性能、高响应性的现代Web应用所必需的。
