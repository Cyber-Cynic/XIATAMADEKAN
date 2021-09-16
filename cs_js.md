### HTML CSS详解
https://www.internetingishard.com/html-and-css/

### HTML: HTML5?
1. 新增元素：语义化更好的标签元素  
结构元素：article、aside、header、hgroup、footer、figure、section、nav  
其他元素：video、audio、canvas、embed、mark、progress、meter、time、command、details、datagrid、keygen、output、source、menu、ruby、wbr、bdi、dialog、

2. 废除的元素：纯表现元素、部分浏览器支持的元素和对可用性产生负面影响的元素  
纯表现元素：basefont、big、center、font、s、strike、tt、u 用css代替  
部分浏览器支持的元素：applet、bgsound、blink、marquee  
对可用性产生负面影响的元素：frameset、frame、noframes,在html5中不支持frame框架，只支持iframe框架  

3. 新增的API
- Canvas
- SVG
- 音频和视频
- Geolocation
- Communication
- XMLHttpRequest Level2
- WebSockets
- Forms：新表单元素tel、email、url、search、range、number 未来的表单元素color、datetime、datetime-local、time、date、week、month
- 新表单特性和函数：placeholder、autocomplete、autofocus、spellcheck、list特性、datalist元素、min和max、step、required
- 拖放API：draggable属性、拖放事件(dragstart、drag、dragenter、dragleave、dragover、drap、dragend)、dataTransfer对象
- Web Workers API
- Web Storage API

### CSS: 盒子模型？
![cssboxmode](https://www.internetingishard.com/html-and-css/css-box-model/css-box-model-73a525.png)

### CSS: block vs inline ?

### CSS: BFC ?
块格式化上下文（Block Formatting Context，BFC） 是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

### CSS: float vs positon ?
![position](https://www.internetingishard.com/html-and-css/floats/floats-and-auto-margin-for-alignment-536a81.png)
![position](https://www.internetingishard.com/html-and-css/advanced-positioning/css-positioning-schemes-790d5b.png)

### CSS: grid vs flex?
CSS网格布局和弹性盒布局的主要区别在于弹性盒布局是为一维布局服务的（沿横向或纵向的），而网格布局是为二维布局服务的（同时沿着横向和纵向）

### CSS: 自适应？
媒体查询（Media queries）  

```
<meta name='viewport' 
     content='width=device-width, initial-scale=1.0, maximum-scale=1.0, 
     user-scalable=0' >
```
```
@media screen and (min-width: 900px) {
  article {
    padding: 1rem 3rem;
  }
}
```

### CSS: less vs sass?
都是CSS预处理器语言  

CSS有具体以下几个缺点：
1. 语法不够强大，比如无法嵌套书写，导致模块化开发中需要书写很多重复的选择器；
2. 没有变量和合理的样式复用机制，使得逻辑上相关的属性值必须以字面量的形式重复输出，导致难以维护。  

使用预处理器的优点
1. 提供CSS层缺失的样式层复用机制
2. 减少冗余代码
3. 提高样式代码的可维护性

Less （Leaner Style Sheets 的缩写） 是一门向后兼容的 CSS 扩展语言。因为 Less 和 CSS 非常像，Less 仅对 CSS 语言增加了少许方便的扩展，学习很容易。  
sass，作为”世界上最成熟、最稳定、最强大的专业级CSS扩展语言”。兼容所有版本的css，且有无数框架使用sass构建，如Compass，Bourbon，和Susy。
### CSS: Lib - BootStrap vs tailwind?

### 基础: ES6
https://es6.ruanyifeng.com/  
https://www.youtube.com/watch?v=n3zrCxB8sj8&list=PLC3y8-rFHvwhI0V5mE9Vu6Nm-nap8EcjV

### 基础: js内存分配 和 垃圾回收？
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Memory_Management

### 基础: js是单线程还是多线程？
单线程。  
如果是单线程为什么能实现异步？  
JavaScript是脚本语言，它需要在一个宿主环境里才能运行，显然我们接触较多的宿主环境就是浏览器。虽说JavaScript是单线程的，然而浏览器却不是！
![browser](https://user-gold-cdn.xitu.io/2020/5/15/172140aad60f19a3?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 基础：宏任务 vs 微任务 ？
异步任务却又分为两种：一种叫“宏任务”(MacroTask 或者 Task)，一种叫“微任务”(MicroTask) 
![task](https://user-gold-cdn.xitu.io/2020/5/15/172141334eeb4d76?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 基础: event loop?
![loop](https://user-gold-cdn.xitu.io/2020/5/15/172141bd83f70cb8?imageslim) 
 
### 基础: 浏览器执行过程？

### 基础: js 基本类型？
最新的 ECMAScript 标准定义了 9 种数据类型:  

6 种原始类型，使用 typeof 运算符检查:  
undefined：typeof instance === "undefined"  
Boolean：typeof instance === "boolean"  
Number：typeof instance === "number"  
String：typeof instance === "string  
BigInt：typeof instance === "bigint"  
Symbol ：typeof instance === "symbol"  

null：typeof instance === "object"。  
Object：typeof instance === "object"。任何 constructed 对象实例的特殊非数据结构类型，也用做数据结构：new Object，new Array，new Map，new Set，new WeakMap，new WeakSet，new Date，和几乎所有通过 new keyword 创建的东西。  
Function：非数据结构，尽管 typeof 操作的结果是：typeof instance === "function"。这个结果是为 Function 的一个特殊缩写，尽管每个 Function 构造器都由 Object 构造器派生。

### 基础: ES6 箭头函数？
箭头函数表达式更适用于那些本来需要匿名函数的地方，并且它不能用作构造函数。  
引入箭头函数有两个方面的作用：```更简短的函数```并且```不绑定this```。  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions

### 基础: let vs var vs const?
var 和 let 用以声明变量，const 用于声明只读的常量；  
var 声明的变量，不存在块级作用域，在全局范围内都有效，let 和 const 声明的，只在它所在的代码块内有效；  
let 和 const 不存在像 var 那样的 “变量提升” 现象，所以 var 定义变量可以先使用，后声明，而 let 和 const 只可先声明，后使用；  
let 声明的变量存在暂时性死区，即只要块级作用域中存在 let，那么它所声明的变量就绑定了这个区域，不再受外部的影响。  
let 不允许在相同作用域内，重复声明同一个变量；  
const 在声明时必须初始化赋值，一旦声明，其声明的值就不允许改变，更不允许重复声明；  

### 基础: Promise?
Promise 是一个对象，它代表了一个异步操作的最终完成或者失败。  
本质上 Promise 是一个函数返回的对象，我们可以在它上面绑定回调函数，这样我们就不需要在一开始把回调函数作为参数传入这个函数了。  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises 

### 基础: 节流防抖？
1. 函数防抖（debounce）：当持续触发事件时，一定时间段内没有再触发事件，事件处理函数才会执行一次，如果设定的时间到来之前，又一次触发了事件，就重新开始延时.
2. 函数节流（throttle）：当持续触发事件时，保证一定时间段内只调用一次事件处理函数。

### 基础: async await?
它们是ECMAScript 2017 JavaScript版的一部分。简单来说，它们是基于```promises的语法糖```，使异步代码更易于编写和阅读。通过使用它们，```异步代码看起来更像是老式同步代码```。  

async:  
将 async 关键字加到函数申明中，可以告诉它们返回的是 promise，而不是直接返回值。  
此外，它避免了同步函数为支持使用 await 带来的任何潜在开销。在函数声明为 async 时，JavaScript引擎会添加必要的处理，以优化你的程序。

await:  
事实上，```await 只在异步函数里面才起作用```。它可以放在任何异步的，基于 promise 的函数之前。它会暂停代码在该行上，直到 promise 完成，然后返回结果值。在暂停的同时，其他正在等待执行的代码就有机会执行了。

### 基础: ts?
TypeScript 有两个主要的目的：  
1. 为 JavaScript 提供一个可选的类型系统  
2. 为当前版本的 JavaScript 引擎提供将来 JavaScript 版本的新功能  

### 基础: settimeout vs setinterval?
setInterval repeats the call, setTimeout only runs it once.

### 基础: 闭包？
一个函数和对其周围状态（lexical environment，词法环境）的引用捆绑在一起（或者说函数被引用包围），这样的组合就是闭包（closure）。  
也就是说，闭包让你可以在一个内层函数中访问到其外层函数的作用域。  
在 JavaScript 中，每当创建一个函数，闭包就会在函数创建的同时被创建出来。  

要理解闭包，首先必须理解Javascript特殊的变量作用域。变量的作用域无非就是两种：```全局变量```和```局部变量```。
函数内部可以直接读取全局变量，在函数外部自然无法读取函数内的局部变量。我们有时候需要得到函数内的局部变量，怎么办？那就是在函数的内部，再定义一个函数。
简单理解就是：```闭包就是能够读取其他函数内部变量的函数。```  

闭包可以用在许多地方。它的最大用处有两个:
1. 可以读取函数内部的变量
2. 让这些变量的值始终保持在内存中

注意：  
1. 由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。
2. 闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。  

https://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html

### 基础: 继承 与 原型链？
当谈到继承时，JavaScript 只有一种结构：对象。  
每个实例对象（ object ）都有一个私有属性（称之为 __proto__ ）指向它的构造函数的原型对象（prototype ）。该原型对象也有一个自己的原型对象( __proto__ ) ，层层向上直到一个对象的原型对象为 null。根据定义，null 没有原型，并作为这个原型链中的最后一个环节。  

js设计之初定位就是简单的脚本语言，没有引入类的概念。  

语言设计者把new命令引入了Javascript，用来从```原型对象```生成一个```实例对象```。但是，Javascript没有"类"，怎么来表示原型对象呢？  
C++和Java使用new命令时，都会调用"类"的构造函数（constructor）。js做了一个简化的设计，在Javascript语言中，new命令后面跟的不是类，而是构造函数。  
用构造函数生成实例对象，有一个缺点，那就是```无法共享属性和方法```。(每一个实例对象，都有自己的属性和方法的副本，不仅无法做到数据共享，也是极大的资源浪费。)  

于是，决定为构造函数设置一个prototype属性。这个属性包含一个对象（简称"prototype对象"），所有实例对象需要共享的属性和方法，都放在这个对象里面；那些不需要共享的属性和方法，就放在构造函数里面。  

由于所有的实例对象共享同一个prototype对象，那么从外界看起来，prototype对象就好像是实例对象的原型，而实例对象则好像"继承"了prototype对象一样。  

这就是Javascript继承机制的设计思想。  

http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html

### 基础: this 作用域？

### 基础: 变量提升（Hoisting）？
JavaScript是单线程语言，所以执行肯定是按顺序执行。但是并不是逐行的分析和执行，而是一段一段地分析执行，会先进行编译阶段然后才是执行阶段。
在编译阶段阶段，代码真正执行前的几毫秒，会检测到所有的变量和函数声明，所有这些函数和变量声明都被添加到名为Lexical Environment的JavaScript数据结构内的内存中。所以这些变量和函数能在它们真正被声明之前使用。  
因为函数声明在编译阶段会被添加到词法环境（Lexical Environment）中，当JavaScript引擎遇到函数时，它会从词法环境中找到这个函数并执行它。  

### 基础: call vs apply?
在 javascript 中，call 和 apply 都是为了改变某个函数运行时的上下文（context）而存在的，换句话说，就是为了改变函数体内部 this 的指向。    
对于 apply、call 二者而言，作用完全一样，只是接受参数的方式不太一样。  
func.call(this, arg1, arg2);  
func.apply(this, [arg1, arg2])  
JavaScript 中，某个函数的参数数量是不固定的，因此要说适用条件的话，当你的参数是明确知道数量时用 call 。  
而不确定的时候用 apply，然后把参数 push 进数组传递进去。当参数数量不确定时，函数内部也可以通过 arguments 这个伪数组来遍历所有的参数。  

### 框架：双向绑定？
双向绑定：数据变化更新视图，视图变化更新数据。  

1. ```视图变化更新数据```我们可以通过```事件监听```的方式来实现
2. ```数据变化更新视图```要将数据变的‘可观测’（借助Object.defineProperty方法。）  
以Vue举例，内部通过Object.defineProperty方法属性拦截的方式，把data对象里每个数据的读写转化成getter/setter，当数据变化时通知视图更新。    
(这就是典型的“发布订阅者”模式，数据变化为“发布者”，依赖对象为“订阅者”)  

总结：
实现数据的双向绑定，首先要对数据进行```劫持监听```，所以我们需要设置一个```监听器Observer```，用来监听所有属性。如果属性发上变化了，就需要告诉订阅者Watcher看是否需要更新。因为订阅者是有很多个，所以我们需要有一个```消息订阅器Dep```来专门收集这些订阅者，然后在监听器Observer和订阅者Watcher之间进行统一管理。

https://my.oschina.net/u/4386652/blog/4281447

### 框架：依赖注入？

### 框架：生命周期？
简单说就是因为需要动态创建界面UI元素，就产生了动态销毁界面UI元素的需求。否则UI元素只增不减迟早拖死应用。  
有了创建和销毁自然就有了生命周期，因为有些事情需要在创建后才能做，有些事情要在销毁的时候做。  
没错，如果不需要动态创建界面UI元素，例如只是切换几个固定的展示页面，或者固定的表单什么的。那么通常也就不需要动态销毁界面UI元素，而使用显示和隐藏来解决。这也是早期前端UI没有生命周期或者说很少提及生命周期的原因……

作者：Ivony
链接：https://www.zhihu.com/question/341446246/answer/798348586
来源：知乎

### 框架：虚拟DOM？diff逻辑？
虚拟DOM简而言之就是，用JS去按照DOM结构来实现的树形结构对象，你也可以叫做DOM对象  
DOM-diff比较两个虚拟DOM的区别，也就是在比较两个对象的区别。  
https://hustyichi.github.io/2020/09/16/vdom/

### 框架：组件?
https://wizardforcel.gitbooks.io/reactjs101/content/Ch03/reactjs-introduction.html

### 工程化：打包构建？
webpack 是一个用于现代 JavaScript 应用程序的 静态模块打包工具。当 webpack 处理应用程序时，它会在内部构建一个 依赖图(dependency graph)，此依赖图对应映射到项目所需的每个模块，并生成一个或多个 bundle。 

https://webpack.docschina.org/
### 全栈：nodejs概念及机制？

### 全栈：NOSQL

### 全栈：页面自动化测试？

### 全栈：单元测试？Mock?

### 全栈：GraphQL & OData?
GraphQL是由 Facebook 在 2012 年创造的一门开源查询语言。
1. Graphql默认就是可以让前端、客户端根据自己的内容需求定制Json语句，然后直接通过一个请求获取到原本需要通过请求多个Restful API才能获取到的内容组合；
2. Restful API接口是一对一，前端、客户端需要多次请求HTTP 接口获取到数据和进行组合，又或者是后端从多个不同Database或者不同人写的数据方法来进行合并数据进行输出。

OData协定，英文全名是Open Data Protocol(OData)，它是一个开源的协定，以简单和标准的方法，来建造或消除可查询和可操作的RESTful API。  
简化了API的命名和组织，便于访问。  

### 网络：HTTP协议？
1. 基于TCP
2. 三次握手
3. 无状态

### 网络：网络抓包？wireshark & fiddler

### 网络：HTTPS？
![https](https://upload-images.jianshu.io/upload_images/11909910-8c2edc6046fbc343.png?imageMogr2/auto-orient/strip|imageView2/2/format/webp)

### 网络：HTTP vs WebSocket?
WebSocket是HTML5规范提出的一种协议，是基于TCP协议的；和HTTP协议是并存的两种协议。  
WebSocket在建立握手时，数据是通过HTTP传输的。但是建立之后，在真正传输时候是不需要HTTP协议的。 
WebSocket是为了解决客户端发起多个http请求到服务器资源浏览器必须要经过长时间的轮训问题而生的，实现了多路复用，是全双工通信   

WebSocket 与 Socket区别？  
Socket其实并不是一个协议，而是为了方便使用TCP或UDP而抽象出来的一层，是位于应用层和传输控制层之间的一组接口。  

### 网络：HTTP请求头部、返回状态码？
HTTP协议的请求和响应报文中必定包含HTTP首部。首部内容为客户端和服务器分别处理请求和响应提供 所需要的信息。  
TTP首部字段根据实际用途被分为以下4种类型。
1. 通用首部字段（General Header Fields）请求报文和响应报文两方都会使用的首部。
2. 请求首部字段（Request Header Fields）从客户端向服务器端发送请求报文时使用的首部。补充了请求的附加内容、客户端信息、响应内容相关优先级等信息。
3. 响应首部字段（ Response Header Fields）从服务器端向客户端返回响应报文时使用的首部。补充了响应的附加内容，也会要求客户端附加额外的内容信息。
4. 实体首部字段（Entity Header Fields）针对请求报文和响应报文的实体部分使用的首部。补充了资源内容更新时间等与实体有关的信息。

https://segmentfault.com/a/1190000010345301  

### web：token?JWT?
token 也称作令牌，由uid+time+sign[+固定参数]  
token 的认证方式类似于临时的证书签名, 并且是一种服务端无状态的认证方式, 非常适合于 REST API 的场景. 所谓无状态就是服务端并不会保存身份认证相关的数据。  

token 的认证流程与cookie很相似  
1. 用户登录，成功后服务器返回Token给客户端。
2. 客户端收到数据后保存在客户端（一般存入localStorage）
2. 客户端再次访问服务器，将token放入headers中
3. 服务器端采用filter过滤器校验。校验成功则返回请求数据，校验失败则返回错误码  

jwt只是一个跨域认证的方案

### web：cookie vs session
1. session 在服务器端，cookie 在客户端（浏览器）
2. session 默认被存在在服务器的一个文件里（不是内存）
3. session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果浏览器禁用了 cookie ，同时 session 也会失效（但是可以通过其它方式实现，比如在 url 中传递 session_id）
4. session 可以放在 文件、数据库、或内存中都可以。
5. 用户验证这种场合一般会用 session

### web安全：XSS?
Cross-Site Scripting（跨站脚本攻击）简称 XSS，是一种代码注入攻击。攻击者通过在目标网站上注入恶意脚本，使之在用户的浏览器上运行。利用这些恶意脚本，攻击者可获取用户的敏感信息如 Cookie、SessionID 等，进而危害数据安全。  

为了和 CSS 区分，这里把攻击的第一个字母改成了 X，于是叫做 XSS。  

XSS 的本质是：恶意代码未经过滤，与网站正常的代码混在一起；浏览器无法分辨哪些脚本是可信的，导致恶意脚本被执行。
### 代码：冒泡排序
```js
var arr = [3, 4, 1, 2];
function bubbleSort (arr) {
  var max = arr.length - 1;
  for (var j = 0; j < max; j++) {
    for (var i = 0; i < max - j; i++) {
      if (arr[i] > arr[i + 1]) {
        var temp = arr[i];
        arr[i] = arr[i + 1];
        arr[i + 1] = temp;
      }
    }
  }
  return arr;
}
bubbleSort(arr);
```

### 代码：斐波那契
```js
function fibonacci(n){
   if(n==0)
    return 0
   else if(n==1)
    return 1
   else 
    return fibonacci(n-1) + fibonacci(n-2)
}
```

尾递归优化：不需要保存栈帧
```js
function FibonacciTailRecursive(int n,int ret1,int ret2)
{
    if(n==0)
       return ret1; 
    return FibonacciTailRecursive(n-1,ret2,ret1+ret2);
}
```

### 工具：浏览器限制网速？浏览器排查请求？

### 工具：postman接口测试？