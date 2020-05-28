# JavaScript/ES6

**一、JS数组常用方法**

|           方法            |                             说明                             |
| :-----------------------: | :----------------------------------------------------------: |
|          push()           |                      添加元素到数组末尾                      |
|           pop()           |                       删除数组末尾元素                       |
|         unshift()         |                     添加元素到数组的头部                     |
|          shift()          |                      删除数组最前面元素                      |
|         indexOf()         |                  查看某个元素在数组中的位置                  |
| splice(start, num, value) | 实现增删改操作（start开始下标，num删除元素个数，value插入或替换的元素） |
|     slice(begin, end)     |                浅拷贝数组并返回拷贝后的新数组                |
|       Array.from()        |       从一个类似数组或可迭代对象中创建一个新的数组实例       |
|  fill(value, start, end)  |         用一个固定值填充数组中[start,end)的全部元素          |

**二、mouseover和mouseenter的区别**

mouseover/mouseout：当鼠标移入元素或其子元素都会触发事件，有一个重复触发的冒泡过程

mouseenter/mouseleave：当鼠标移入元素本身（不包含元素的子元素）会触发事件，即不会冒泡

**三、clientHeight, scrollHeight, offsetHeight ,以及scrollTop, offsetTop, clientTop的区别？**

clientHeight：可视区域高度，不包含border和滚动条  
offsetHeight： 可视区域高度，包含border和滚动条  
scrollHeight：所有区域高度，包含因滚动被隐藏的部分  
clientTop：边框border的厚度  
scrollTop：滚动后被隐藏的高度，获取对象最顶端与窗口中可见内容最顶端之间的距离  
offsetTop：获取指定对象相对于版面或布局中设置position属性的父容器顶端位置的距离

<img src="\Images\浏览器宽高.jpg" style="zoom:80%;" />

**四、JS类型判断**

typeof A、A instanceof B、Object.prototype.toString.call (A)

注意：数组判断不能用typeof（typeof只能判断是否是object）

**五、如何获得对象上的属性**

- for(let l in obj)：遍历一个对象及其原型链中所有可枚举的属性
- object.keys：返回一个包含所有可枚举的属性名称的数组
- object.getOwnPropertyNames：返回一个包含不可枚举的属性的数组（基本包装类型的原型属性不可枚举，如Object、Array、Number等）

**六、JS语言特点**

- 运行在客户端浏览器上
- 不用预编译，直接解析执行代码
- 弱类型语言，较为灵活
- 与操作系统无关，跨平台
- 脚本语言、解释性语言

**七、JS中string的startswith和indexof两种方法的区别**

- str.startsWith(searchString, position)  
searchString：要搜素的子字符串  
  position（可选）：搜索searchString的开始位置，默认为0  
能找到返回true，找不到返回false
  
- str.indexOf(searchValue, fromIndex)  
searchValue：要搜索的字符串  
  fromIndex（可选）：开始查找的位置，默认为0  
没找到返回-1，否则返回searchValue第一次出现的索引

**八、ES6有哪些新特性？**

- 新增let、const声明变量，实现了块级作用域
- 新增箭头函数
- 引入promise、await/async解决异步回调问题
- 引入Class作为对象的模板，实现更好的面向对象编程
- 引入模块方便模块化编程
- 引入新的数据类型symbol，新的数据结构set和map

**九、let、const、var区别**

| 类型  | 变量提升 | 暂时性死区 | 重复声明 | 初始值 |         作用域         |
| :---: | :------: | :--------: | :------: | :----: | :--------------------: |
|  var  |   存在   |   不存在   |   允许   | 不需要 | 全局作用域、函数作用域 |
|  let  |  不存在  |    存在    |  不允许  | 不需要 |       块级作用域       |
| const |  不存在  |    存在    |  不允许  |  需要  |       块级作用域       |

变量提升：变量可在声明前使用  
暂时性死区：代码块内，使用let、const声明变量之前，该变量都是不可用的

**十、==和===、以及Object.is的区别**

==：两边值类型不同时，强制转换成number再进行比较（null==undefined→true）

===：严格比较运算符，不会进行强制类型转换（+0===-0  true；NaN===NaN  false）

Object.is()：与===基本一致（Object.is(+0,-0)  false；Object.is(NaN,NaN)  true）

**十一、setTimeout、setInterval和requestAnimationFrame**

|           名称            |                             说明                             |
| :-----------------------: | :----------------------------------------------------------: |
|  setTimeout/clearTimeout  |                     延时执行参数指定代码                     |
| setInterval/clearInterval |                   每隔一段时间执行指定代码                   |
|   requestAnimationFrame   | 在浏览器每次刷新页面之前执行：1. 会把每一帧中所有的DOM操作集中起来，在一次重绘或回流中就完成，并且重绘或回流的时间间隔紧紧跟随浏览器的刷新频率；2. 对于隐藏元素不会进行重绘或回流，减少了CPU、GPU和内存使用量；3. 由浏览器专门为动画提供的API，在运行时浏览器会自动优化方法的调用；页面如果不是激活状态，动画会暂停播放，有效节省了CPU开销 |

**十二、高频度触发事件的优化方案**

| 方案         | 说明                                       | 应用场景                   |
| ------------ | ------------------------------------------ | -------------------------- |
| 防抖debounce | 抖动结束的时间超过指定时间间隔时才执行任务 | 搜索联想、窗口resize       |
| 节流throttle | 指定时间间隔内只执行一次任务               | 滚动事件、鼠标不断点击触发 |

**十三、JS类有哪几种继承方式？各有什么特点？**

- 原型链继承：将父类实例作为子类原型  
特点：基于原型链，既是父类的实例，又是子类的实例  
  缺点：无法实现多继承，无法向父类构造参数传参

- 构造继承：使用父类的构造函数来增强子类实例  
特点：可以实现多继承  
  缺点：只能继承父类的实例属性和方法，不能继承原型上的属性和方法

- 实例继承：为父类实例添加新特性，作为子类实例返回  
特点：不限制调用方法  
  缺点：实例是父类的实例，不是子类的实例，不支持多继承

- 拷贝继承：拷贝父类元素上的属性和方法  
特点：支持多继承  
  缺点：效率低、内存占用高

- 组合继承：构造继承+原型链继承  
特点：可以继承实例属性和方法，也可以继承原型属性和方法  
  缺点：调用两次父类构造函数，会生成两份实例

- 寄生组合继承：通过寄生方式，砍掉组合继承中父类的实例属性  
  特点：避免组合继承中初始化两次实例方法和属性

  参考：[说一下类的创建和继承](https://github.com/jinzita007/studies/issues/2)	[JS原型链与继承别再被问倒了](https://juejin.im/post/58f94c9bb123db411953691b#heading-8)

**十四、js的new操作符做了哪些事情**

1. 创建一个类的实例：创建一个空对象obj，将obj._proto_设置为构造函数的prototype
2. 初始化实例：构造函数被传入参数并调用，this指针被设定为指向该实例obj
3. 返回实例obj

**十五、改变函数内部this指针可以使用哪些函数？有什么区别？**

- call()：第一个参数为要改变指向的对象，之后的参数为arg1，arg2…，函数立即执行
- apply()：第一个参数为要改变指向的对象，之后的参数为一个数组arguments，函数立即执行
- bind()：返回一个新的函数，函数不会立即执行

call和apply作用：改变this的指向；借用别的对象的方法；调用函数

**十六、如何解决js加载过程阻塞问题？**

1. 将script标签放到body底部：此时DOM已加载完毕因此不存在阻塞问题（并非异步策略）

2. 异步加载外部js文件：defer、async

   defer属性：给script标签设置defer属性，将脚本文件设置为延迟加载，遇到带有defer属性的script标签时，浏览器会再开启一个线程去下载js文件，同时继续解析HTML文档，等HTML全部解析完毕DOM加载完成后，再去执行加载好的js文件，可以保证多个js文件的执行顺序就是它们在页面中的出现顺序  
async属性：类似于defer属性，但与defer不同的是，它会在下载完毕后立刻执行。对于多个带有async的js文件，不保证按顺序执行，哪个js文件先下载完就先执行哪个

**十七、什么是闭包？闭包有什么用？** 

闭包：能够访问其他函数作用域中的变量的函数

应用：模仿块级作用域；保存外部函数的变量；封装私有变量（单例模式）

闭包与堆内存：闭包中的变量并不保存在栈内存中，而是保存在堆内存中，所以函数调用之后闭包还能引用到函数内的变量

**十八、什么是立即执行函数（IIFE）？有何特点？有什么用处？**

(function(){  
//执行语句  
})();

特点：立即执行函数中的代码，又不会在内存中留下对该函数的引用；函数内部的所有变量都会被立即销毁（除非这些变量赋值给了包含作用域中的变量）  
作用：实现块级作用域

**十九、如何理解前端模块化**
模块化思想：隔离不同的js文件，仅暴露当前模块所需要的其他模块

将复杂的文件编成一个个独立的模块，有利于复用和维护。但会产生模块之间相互依赖的问题，可通过js打包工具webpack解决

**二十、ES6模块化**

1.	ES6模块中自动采用严格模式，规定：
   - 变量必须先声明
   - 函数参数不能有同名属性
   - 禁止this指向全局
   - 对只读属性赋值、删除不可删除属性直接报错
   - arguments不可重新赋值，不会自动反应函数参数变化
   - 增加保留字static、interface、producted等
2.	export
   export语句输出的接口是对应值的引用，也就是一种动态绑定关系，通过该接口可以获取模块内部实时的值；export命令要处于模块顶层
   - 把export直接加到声明前面
   - export {a, b, c}
   - export default默认导出（一个js文件中只能有一个默认导出，但可以导出多个方法）
3.	import
   import是静态执行，Singleton模式；import命令要处于模块顶层
   - import {XX} from ‘./test.js’
   - import {XX as YY} from ‘./test.js’  
   - import * as YY from ‘./test.js’

**二十一、webpack用来干什么的**
js应用程序的静态模块打包器。当用webpack处理应用程序时，它会递归地构建一个依赖关系图，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个bundle

**二十二、JS垃圾回收的两种方法**

- 标记清除：总体思想是将寻找不再使用的对象变为寻找无法到达的对象，即从根部（全局对象）出发定时扫描内存中的对象，凡是能从根部到达的对象都是还需要使用的。

  1. 垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记

  2. 从根部出发将能触及到的对象的标记清除

  3. 还存在标记的变量被视为准备删除的变量

  4. 垃圾收集器执行最后一步内存清除工作，销毁那些带标记的值并回收它们所占用的内存空间

- 引用计数：统计引用类型变量声明后被引用次数，当次数为0时该变量被回收。

**二十三、什么是内存泄露？常见的内存泄露有哪些？如何避免？**

1. 定义：由于疏忽或错误造成程序未能释放那些已经不再使用的内存，造成内存的浪费

2. 案例：

   - 由于未声明而意外产生的全局变量

   - 没有回收的定时器和回调函数

   - 闭包（闭包之间是共享作用域的）

   - DOM元素的引用

3. 解决方案：

   - 减少不必要的全局变量，使用严格模式避免意外创建全局变量

   - 使用完数据后及时解除引用（DOM引用、闭包中的变量、定时器清除）

   - 组织好函数逻辑，避免死循环等造成浏览器卡顿和崩溃

参考：[「前端进阶」JS中的内存管理](https://juejin.im/post/5d0706a6f265da1bc23f77a9)

**二十四、js内存空间**

- 栈：存放变量

- 堆：存放复杂对象

- 池（一般也归类为栈中）：存放常量

栈内存由于自身数据结构的特点，系统效率较高；堆内存需要分配空间和地址，还要把地址存到栈中，所以效率低于栈

**二十五、js基本数据类型有哪些？引用数据类型有哪些？基本数据类型和引用数据类型的区别？**
基本数据类型：null、undefined、symbol、boolean、string、number

引用数据类型：Object、Array、RegExp、Date、Function、特殊的基本包装类型（String、Number、Boolean）、单体内置对象（Global、Math）

区别：

1. 基本数据类型的比较是值的比较；引用数据类型比较的是内存地址是否相同

2. 基本数据类型存放在栈区；引用数据类型同时存放在栈区和堆区
   
3. 基本数据类型的赋值是简单赋值；引用数据类型赋值是对象引用

4. 基本数据类型不能添加引用和方法；引用数据类型可以

**二十六、变量类型与内存的关系**

- 基本数据类型存放在栈区（栈内存中的变量一般在其当前执行环境结束就会被销毁和回收）
  
  基本数据类型占用空间小、大小固定，按值访问，属于被频繁使用的数据。
  
- 引用数据类型存放在栈区和堆区（堆内存中的变量只有在所有对它的引用都结束时才会被回收）
  
  引用数据类型占用空间大、大小不固定，若存储在栈中会影响程序运行的性能；但引用数据类型的指针存储在栈中，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会先检索其在栈中的地址，取得地址后再从堆中获得实体。

**二十七、跨域原理？js实现跨域**
跨域：浏览器不能执行其他网站的脚本，是由浏览器的同源策略造成的，是浏览器对JS实施的安全限制  
（只要协议、域名、端口有任何一个不同，都被当作是不同的域）

跨域原理：通过各种方式避开浏览器的安全限制

实现方法：CORS；代理服务器；JSONP；document.domain+iframe；location.hash+iframe；window.name+iframe；postMessage 

**二十八、什么是symbol**
ES6新增属性，Symbol(description)函数生成一个全局唯一的值，能够作为对象属性的标识符；description为字符串类型，仅作为对symbol的描述，相当于一个注释。

**二十九、this的指向有哪几种**

- 默认绑定：全局环境中this默认绑定到window
- 隐式绑定：被直接对象所包含的函数调用时，即方法调用时，this隐式绑定到该对象上
- 隐式丢失：被隐式绑定的函数丢失绑定对象时，会默认绑定到window
- 显示绑定：通过call()、apply()、bind()方法把对象绑定到this上
- new绑定：函数或方法调用前带有关键字new，就构成构造函数调用，对于this绑定来说，称为new绑定

**三十、ES6箭头函数与普通函数的区别**

1. 箭头函数没有this，需要通过查找作用域链来确定this的值，即如果箭头函数被非箭头函数包含，this绑定的就是最近一层非箭头函数的this
2. 箭头函数没有自己的arguments对象，但是可以访问外围函数的arguments对象
3. 不能通过new关键字调用，无原型

**三十一、js原型链，原型链的顶端是什么？Object的原型是什么？Object的原型的原型是什么？**

<img src="\Images\原型链.jpg" style="zoom:80%;" />

注：蓝色部分为原型链

**三十二、为什么js是单线程？**
JavaScript作为浏览器脚本语言，主要用途是与用户互动，以及操作DOM，这决定了它只能是单线程，否则会带来很复杂的同步问题。比如若js同时拥有两个线程，一个线程在某个DOM节点上添加内容，另一个线程删除这个节点，那浏览器将不知所措。为了利用多核CPU的计算能力，HTML5提出Web Worker标准，允许JS脚本创建多个线程，但子线程完全受主线程控制，且不得操作DOM，所以该标准并没有改变JS单线程的本质。

**三十三、什么是Web Worker？使用Web Worker有什么注意点？**
Web Worker的作用是为JS创建多线程环境，允许主线程创建Worker线程，将一些任务分配给线程运行。主线程运行的同时，Worker线程在后台运行，两者互不干扰；Worker线程完成计算任务后，再把结果返回给主线程。

注意点：

- 同源限制：分配给worker线程运行的脚本文件必须和主线程的脚本文件同源
- DOM限制：worker线程无法读取主线程所在网页的DOM对象，无法使用document、window对象，但可以使用navigator、location对象
- 通信限制：worker线程和主线程不在同一上下文环境，不能直接通信，须通过消息完成
- 文件限制：worker线程无法读取本地文件，所加载的脚本必须来自网络

**三十四、什么是事件委托/事件代理？典型例子？**
定义：不在事件发生的直接DOM上设置监听函数，而在其父元素上设置监听函数，通过事件冒泡，父元素可以监听到子元素上事件的触发，通过判断事件发生元素DOM的类型（使用target属性），来做出不同的响应。

好处：新增子对象时无需再次对其绑定事件，适合动态添加元素；减少事件注册，减少内存消耗。

举例：ul和li标签的事件监听（不在li标签上直接添加事件监听而是在ul标签上添加）

**三十五、什么是事件监听**
element.addEventListener(event, function, useCapture) 用于向指定元素添加事件
event：事件类型，如click、scroll、mousedown、resize等
function：事件触发后调用的函数
useCapture：描述事件传递方式，可选。默认为false即冒泡传递；true时为捕获传递

**三十六、什么是promise？** 

1. Promise是一个构造函数，用来生成promise实例  
2. 构造函数接收一个参数，这个参数是一个函数，当创建实例的时候，该作为参数的函数里的内容会立即执行
3. 参数里面的函数又接收两个参数，两个参数均为函数，一个为resolve，一个为reject
4. 异步操作成功时调用resolve，resolve函数将promise对象的状态从pending变为resolved并将结果作为参数传出去
5. 异步操作失败时调用reject，reject函数将promise对象的状态从pending变为rejected，并将操作报出的错误作为结果传递出去
6. 实例生成后，可以用then方法分别指定resolved状态和rejected状态的回调函数
7. then方法接收两个函数作为参数，分别为resolved和rejected的回调函数，第二个参数可选
8. catch方法在then方法后调用，发生错误时调用，本质上等同于then(null, rejected);

Promise特点：
   - 三种状态：pending、resolved（fulfilled）、rejected
   - 对象的状态不受外部影响，只有异步操作的结果才能决定当前是哪一种状
   - 一旦状态改变就凝固了，不会再改变（pending→resolved；pending→rejected）

参考：[ES6基础之详解Promise基本用法](https://blog.csdn.net/zhy13087344578/article/details/78132105)

**三十七、async和await如何使用？** 
async关键字用于声明一个function是异步的，被async修饰的函数返回的是一个promise；await只能在async函数中使用，用于等待一个异步方法执行完成，await等待的内容可以是常量、变量、promise、函数等。

async/await中的错误处理：使用try-catch来错误捕捉；使用promise的catch来错误捕捉

参考：[理解async/await](https://juejin.im/post/5d9e8539f265da5b8a515e63)

**三十八、说一下JS的事件模型**

1. 事件模型

   - DOM0事件模型/原始事件模型：事件不会传播，仅作为元素的一个属性
     
     直接在HTML中绑定： 
     ```
   <input type="button" onclick="fun()">
     ```
     
     通过js代码指定属性值：
     ```
     var btn = document.getElementById('.btn'); btn.onclick = fun;
     ```
     移除监听函数：
     
     ```
     btn.onclick=null;
     ```
     
   - IE事件模型：事件处理阶段→事件冒泡阶段（目标元素→document）
     绑定：attachEvent(eventType, handler)
     移除：detachEvent(eventType, handler)

   - DOM2事件模型：事件捕获阶段→事件处理阶段→事件冒泡阶段（document→目标元素→document）
     绑定：addEventListener(eventType, handler, useCapture)
     移除：removeEventListener(eventType, handler, useCapture)

2. 事件对象
   - DOM事件模型中的事件对象常用属性
     type获取事件类型
     target获取事件的目标节点
     stopPropagation()阻止捕获和冒泡阶段中当前事件的进一步传播
     preventDefault()阻止事件默认行为而不停止事件的进一步传播

   - IE事件模型中的事件对象常用属性
     type获取事件类型
     srcElement获取事件目标
     cancelBubble阻止事件冒泡
     returnValue阻止事件默认行为

3. 执行顺序

   如果一个DOM节点同时绑定了多个事件监听函数，且有的用于捕获，有的用于冒泡，则绑定在被点击元素上的事件是按照代码添加顺序执行的，其他先捕获再冒泡。

**三十九、浏览器中的Event Loop事件循环**

JavaScript：单线程（代码执行时只有一个主线程来处理所有任务）非阻塞（当代码需要进行一项异步任务时，主线程挂起该任务，然后在异步任务返回结果的时候再根据一定规则去执行相应的回调→Event Loop）

<img src="\Images\浏览器事件循环.png" style="zoom:80%;" />

1. 任务队列

   - Macrotask（宏任务）：script（整体代码）、setTimeout、setInterval、I/O、UI交互事件、postMessage、MessageChannel  
   - Microtask（微任务）：Promise.then、Object.observe

2. 事件循环执行流程

   一次事件循环只执行位于Macrotask队首的任务，执行完成后立即执行Microtask队列中的所有任务（一开始在js主线程中跑的任务就是Macrotask任务，因此执行完主线程的代码后，会从Microtask队列中取任务来执行）

3. 定时器问题：setTimeout不保证可靠定时

   定时器中设置的时间仅保证任务会在delay毫秒后进入Macrotask队列，并不意味着它能立刻运行，因为可能当前主线程正在进行一个耗时的操作，也可能目前Microtask队列中有很多个任务。

4. Js是阻塞还是非阻塞的？

   核心是同步阻塞，而对于js异步事件，因为有事件循环机制，所以异步事件就是由事件驱动异步非阻塞的

5. requestAnimationFrame既不属于Microtask也不属于Macrotask

   同步任务→promise等微任务→制作render树→requestAnimationFrame→制作render树→第一帧重绘完成→setTimeout等宏任务

**四十、Node中的Event Loop事件循环**

1. Node简介

   Node.js采用V8作为js的解析引擎，而I/O处理方面使用libuv，libuv是一个基于事件驱动的跨平台抽象层，封装了不同操作系统一些底层特性，对外提供统一的API，事件循环机制由它实现

2. Node.js运行机制

   - V8引擎解析JavaScript脚本
   - 解析后的代码调用Node API
   - libuv库负责Node API的执行，它将不同的任务分配给不同的线程，形成一个事件循环，以异步的方式将任务的执行结果返回给V8引擎
   - V8引擎将结果返回用户

![](\Images\Node.png)

3. 事件循环六个阶段

   libuv中的事件循环分六个阶段，它们会按照顺序反复运行，每当进入某一个阶段的时候，都会从对应的回调队列中取出函数去执行。当队列为空或者执行的回调函数数量达到系统设定的阈值，就会进入下一阶段。

   ![](\Images\node事件循环.jpg)

   - timers阶段  
     执行setTimeout()、setInterval()的回调，由poll阶段控制（与浏览器不同，timers阶段有几个setTimeout、setInterval都会依次执行）
   
   - I/O callbacks阶段：处理上一轮循环中少数未执行的I/O回调
   
   - idle，prepare阶段：仅node内部使用
   
   - poll阶段  
     获取新的I/O事件，适当的条件下node将阻塞在这里。该阶段系统会做两件事：回到timer阶段执行回调；执行I/O回调。在进入该阶段时： 
   
     如果没有设定timer，则：1.若poll队列不为空，会遍历回调队列并同步执行，直到队列为空或者达到系统限制；2.若poll队列为空，则（1）若有setImmediate回调需要执行，poll阶段会停止并且进入到check阶段执行回调；（2）若没有setImmediate回调需要执行，会等待回调被加入到队列中并立即执行回调，同时会有个超时时间防止死等。  
   
     如果设定了timer且poll队列为空，则会判断是否有timer超时，如果有的话会回到timer阶段执行回调
   
   - check阶段：执行setImmediate()的回调

   - close callbacks阶段：执行socket的close事件回调

4. MicroTask与MacroTask

   MacroTask：setTimeout、setInterval、setImmediate、script（整体代码）、I/O操作  
   MicroTask：process.nextTick、Promise().then

5. 注意点

   setTimeout和setImmediate  
   两者调用时机不同，setImmediate设计在poll阶段完成时执行，即check阶段；setTimeout设计在poll阶段为空闲时，且设定时间达到后在timer阶段执行。二者在异步I/O callbacks内部调用时，总是先执行setImmediate再执行setTimeout；其他情况先后顺序不一定（setTimeout(func, 0)===setTimeout(func, 1)，如果在准备时候花费时间大于1ms，则在timers阶段就会直接执行setTimeout回调，小于1ms先执行setImmediate回调）

   process.nextTick  
   独立于Event Loop之外，有一个自己的队列，当每个阶段完成后如果存在nextTick队列，就会转而清空nextTick队列中的所有回调函数，且优先于其他microtask执行

**四十一、Node与浏览器的Event Loop差异**

Microtask任务队列的执行时机不同

- Node端：microtask在事件循环的各个阶段之间执行
- 浏览器端：microtask在事件循环的macrotask执行完之后执行

![](\Images\事件循环差异.png)

参考：

[面试一定会问到的-js事件循环](https://juejin.im/post/5da742936fb9a04e223333ff)

[浏览器与Node的事件循环(Event Loop)有何区别?](https://juejin.im/post/5c337ae06fb9a049bc4cd218)

[【js事件循环】+ requestAnimationFrame与页面绘制在事件循环中的顺序关系](https://blog.csdn.net/weixin_42476799/article/details/102893692)

**四十二、说说C++，Java，JavaScript这三种语言的区别**

- 静态类型/动态类型

  C++、Java属于静态类型语言，编译的时候就能够知道每个变量的类型，编程时需给定类型；js属于动态类型语言，运行的时候才知道每个变量的类型，编程的时候无需显示指定的类型

- 编译型/解释型

  C++是编译型语言，需要编译器编译成本地可执行程序后才能运行，用户只使用编译好的本地代码；js是解释型语言，用户直接使用脚本解释器将脚本文件解释执行；Java分为两个阶段，首先像C++一样经过编译器编译，但生成字节码（与平台无关），然后由Java虚拟机运行字节码，使用解释器执行这些代码

- js和Java的区别：

  Java编译字节码阶段和执行阶段是分开的，即编译阶段时间长短无所谓；对于js这些都是在网页和js文件下载后同执行阶段一起在网页的加载和渲染过程中实施的，所以对处理时间有严格要求