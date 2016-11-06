# Welcome to the Front-End-Developer-Questions wiki!

# 目录
* 1. [JavaScript部分](#JavaScript)
* 2. [CSS部分] (#css)
* 3. [HTML部分] (#HTML)

<a name="JavaScript"></a>
# JavaScript部分
* Q1：介绍JavaScript的基本数据类型。
> ES5下共有六种：Undefined，Null，Boolean，Number和String，还含有一种复杂数据类型—Object  

* Q2：JavaScript原型，原型链 ? 有什么特点？  
  > 1.JS中每个函数都存在有一个原型对象属性prototype。并且所有函数的默认原型都是Object的实例。  
  > 2.每个继承父函数的子函数的对象都包含一个内部属性_proto_。该属性包含一个指针，指向父函数的prototype。若父函数的原型对象的_proto_属性为再上一层函数。在此过程中就形成了原型链。  
  > 3.原型链实现了继承。原型链存在两个问题：a 包含引用类型值的原型属性会被所有实例共享。b 在创建子类型时，无法向超类型的构造函数中传递参数。特点：JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的话，就会查找他的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象。
 
* Q3：JavaScript有几种类型的值？（堆：原始数据类型和 栈：引用数据类型），你能画一下他们的内存图吗？
  > 基本数据类型存储在栈中，引用数据类型（对象）存储在堆中，指针放在栈中。两种类型的区别是：存储位置不同；原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体。

* Q4：Javascript如何实现继承？
> 构造继承，原型继承，（实例继承，拷贝继承）。构造函数继承可以将构造函数的属性拷贝给实例（＊.call(this,[])）。但是缺点是无法实现函数复用。原型继承可以实现函数复用，但是所有实例共享一个属性，任意一个实例改变原型属性都会改变其它实例的属性值。推荐采用构造函数继承传递属性（拷贝），原型继承传递方法.

* Q5：Javascript创建对象的几种方式？
  >1.对象字面量的方式p＝｛｝；2.用function来模拟无参的构造函数，再定义属性；3.用function模拟构造函数，利用this；4.利用工厂方式（内置对象Object）；5.利用原型方式来创建；6.混合方式来创建。  

* Q6：Javascript作用链域?
>当代码在一个环境中执行时，会创建变量对象的一个作用域链。如果是个函数，则将其活动对象作为变量对象。活动对象在最开始只包含一个arguments对象。而下一个变量对象则来自下一个包含环境。如此一直延续到全局执行环境，这种组织形式即为作用域链。内部函数可访问外部变量，外部变量无法访问内部函数。注意：js没有块级作用域，若要形成块级作用域，可通过`（function（）｛｝）（）`；立即执行的形式实现。

* Q7：谈谈This对象的理解？
> this总是指向函数的直接调用者（而非间接调用者）；  
如果有new关键字，this指向new出来的那个对象；  
在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window

* Q8：eval是做什么的？
> 计算某个字符串，并执行其中的的 JavaScript 代码。eval(string)。应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');

* Q9：什么是window对象? 什么是document对象?
> Window对象代表浏览器中打开的一个窗口。document对象代表整个HTML文档。实际上，document对象是window对象的对象属性。

* Q10：null，undefined的区别？
> null表示一个对象被定义了，但存放的是空指针。  
undefined 表示这个值不存在。typeof（null）－object；typeof（undefined）－undefined。

* Q11：["1", "2", "3"].map(parseInt) 答案是多少？
>  [1,NAN,NAN]

* Q12：什么是闭包（closure），为什么要用它？
>闭包指的是一个函数可以访问另一个函数作用域中变量的函数。常见的构造方法，是在一个函数内部定义另外一个函数。内部函数可以引用外层的参数和变量；参数和变量不会被垃圾回收机制回收。注意，闭包的原理是作用域链，所以闭包访问的上级作用域中的变量是个对象，其值为其运算结束后的最后一个值。除非用立即执行函数来解决。    
闭包常用的两种应用方式：_**1）函数作为返回值； 2）函数作为方法的参数**_

* javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？
> use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。目前支持的浏览器为IE10+，Firefox 4+，Safari 5.1+和Chrome。默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;提高编译器效率，增加运行速度；为未来新版本的Javascript标准化做铺垫。

* 如何判断一个对象是否属于某个类？
> 使用instanceof 即if(p instanceof Person){alert('yes');} ；判断数据类型则用typeof

* new操作符具体干了什么呢?
> 1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。p._proto_ = Base.prototype;  
2、属性和方法被加入到 this 引用的对象中。Base.call(p/this)  
3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。  

* 说说JavaScript的基本规范  
 >(1)不要在同一行声明多个变量。

  >(2)请使用 ===/!==来比较true/false或者数值

  >(3)使用对象字面量替代new Array这种形式

  >(4)不要使用全局函数。

  >(5)Switch语句必须带有default分支

  >(6)函数不应该有时候有返回值，有时候没有返回值。

  >(7)For循环必须使用大括号

  >(8)If语句必须使用大括号

  >(9)for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。


* 用原生JavaScript的实现过什么功能吗？
> 做过一些插件：图片轮播

* Javascript中，有一个函数，执行对象查找时，永远不会去查找原型，这个函数是？
> Object.hasOwnProperty(proName)，用于检查对象是否含有某个属性。

* 对JSON的了解？
> 一种数据格式；常用两个函数：JSON.parse(str)（讲str变为json对象）;JSON.stringify(obj)则与前面相反;

* [].forEach.call($$("*"),function(a){ a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16) }) 能解释一下这段代码的意思吗？
> 获取页面中所有的元素，然后遍历每个元素，为元素的style属性增加一个颜色边框。

* js延迟加载的方式有哪些？
> defer和async属性、动态创建DOM方式（用得最多）、按需异步载入js。注：（setTimeOut（js，time））

* Ajax 是什么? 如何创建一个Ajax？
> ajax的全称：Asynchronous Javascript And XML。所谓异步，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验

* 同步和异步的区别?
> 同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.  
同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,进行下一步操作。  
异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

* 如何解决跨域问题?
> 数据格式：jsonp,CORS。  
> 
> Ajax注意点：  
> HTTP请求过程：  
> 1.建立TCP连接。  
> 2.Web浏览器向Web服务器发送请求命令。  
> 3.Web浏览器发送请求头信息。  
> 4.Web服务器应答。5.Web服务器发送应答头信息。  
> 6.Web服务器向浏览器发送数据。  
> 7.Web服务器关闭TCP连接。  

> HTTP请求内容：  
> 1.HTTP请求的方法或动作。  
> 2.正在请求的URL。  
> 3.请求头，包含一些客户端环境信息。  
> 4.请求体，客户提交的查询字符串信息和表单信息。   

> GET 信息获取，使用URL传递参数，发送信息数量限制在2000字符内。获取的数据存放在cache中。  
  POST 信息修改，对发送信息数量无限制。用send(data)，注意头文件setRequestHeader。   
  
    request.onreadystatechange = function(){  
  		if(request.readyState ==4){
			if(request.status == 200){
 				document.getElementById("searchResult").innerHTML = request.responseText;
   			}else{ 
				alert("发生错误："＋request.status);
			}
        }
    }  

> HTTP状态码（status）:  
> 1XX：信息类，表示收到Web浏览器请求，正在进一步的处理中。    
> 2XX：成功，表示用户请求被正确接收，理解和处理。    
> 3XX：重定向，表示请求没有成功，客户必须采取进一步的动作。    
> 4XX：客户端错误，表示客户端提交的请求有错误。    
> 5XX：服务器错误，表示服务器不能完成对请求的处理。    
> readyState属性：0:请求未初始化；1:服务器连接已建立。2:请求已接收。3:请求处理中。4:请求完成。  
> JSON采用键值对来编写。json的长度和xml格式化比起来很短小。json读写的速度更快。json可以用js内建的方法直接解析，转换成js对象。  

* 页面编码和被请求的资源编码如果不一致如何处理？
> 若请求的资源编码，如外引js文件编码与页面编码不同。可根据外引资源编码方式定义为charset="utf-8"或"gbk"。

* 模块化开发怎么做？
> 参考[http://blog.chinaunix.NET/uid-26672038-id-4112229.html](http://blog.chinaunix.NET/uid-26672038-id-4112229.html)

* AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？
> (1) 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.  
(2)CMD 推崇依赖就近，AMD 推崇依赖前置。

* requireJS的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何 缓存的？）

* 让你自己设计实现一个requireJS，你会怎么做？

* 谈一谈你对ECMAScript6的了解？  
	1. 1 默认参数
	> 以前参数赋值要在函数体内，但在ES6中，可以：  
	> var link = function(height = 50, color = 'red', url = 'http://azat.co') {  
		  		...  
		}  
	
	1. 2 Template Literals（模板对象）  
	> 在ES6中，我们可以使用新的语法$ {NAME}，并把它放在反引号里  
	> 以前：  
	> 
	>     var name = 'Your name is ' + first + ' ' + last + '.';   
	>     var url = 'http://localhost:3000/api/messages/' + id;  

	> 现在：  
	>   
	>     var name = `Your name is ${first} ${last}. `;  
	>     var url = `http://localhost:3000/api/messages/${id}`;

	1. 3 Multi-line Strings （多行字符串）  
	> 现在用反引号就可以，如：  
	>   
	>       var fourAgreements = `You have the right to be you.  
	>       You can only be you when you do your best.`;  
	
	1. 4 **Destructuring Assignment** （解构赋值）in ES6

	> 解构可能是一个比较难以掌握的概念。先从一个简单的赋值讲起，其中house 和 mouse是key，同时house 和
	> mouse也是一个变量，在ES5中是这样：

	>     var data = $('body').data(), // data has properties house and mouse
    		house = data.house,
    		mouse = data.mouse;  
	>
	> 以及在node.js中用ES5是这样：
	> 
	>     var jsonMiddleware = require('body-parser').jsonMiddleware ;
	>     var body = req.body, // body has username and password   
	>     username = body.username,
	>     password = body.password;  
	>
	> 在ES6，我们可以使用这些语句代替上面的ES5代码：
	> 
	>     var { house, mouse} = $('body').data(); // we'll get house and mouse    variables
	>     var {jsonMiddleware} = require('body-parser');
	>     var {username, password} = req.body;  
	> 
	> 这个同样也适用于数组，非常赞的用法：
	> 
	>     var [col1, col2]  = $('.column'),
	>     [line1, line2, line3, , line5] = file.split('n');  
	>
	> 我们可能需要一些时间来习惯解构赋值语法的使用，但是它确实能给我们带来许多意外的收获。  
	> 
	1. 5 **Enhanced Object Literals** （增强的对象字面量）in ES6
	>
	1. 6 **Arrow Functions**（箭头函数） ES6  
	> 有了箭头函数在ES6中， 我们就不必用that = this或 self = this 或 _this = this 或.bind(this)。例如，下面的代码用ES5就不是很优雅：  
	>   
	>     var _this = this;
    	$('.btn').click(function(event){
    	  _this.sendData();
    	})  

	在ES6中就不需要用 _this = this：  

	    $('.btn').click((event) =>{
    	  this.sendData();
    	})  
	1. 7 Promises
	>
	1. 8 **Block-Scoped Constructs Let and Const**（块作用域和构造let和const）  
	>
	1. 9 **Classes** （类）in ES6
	>
	1. 10 **Modules** （模块）  
>

* ECMAScript6 怎么写class么，为什么会出现class这种东西?  
	> 利用关键字 class ，添加一个构造函数来实现了，举例如下：  
	> 
		class baseModel {
		  	constructor(options, data) { // class constructor，node.js 5.6暂时不支options= {}, data = []这样传参
			this.name = 'Base';
			this.url = 'http://azat.co/api';
			this.data = data;
			this.options = options;
		   }
			getName() { // class method
				console.log(`Class name: ${this.name}`);
			}
		}  

	> 使用extend来继承:

* 异步加载的方式有哪些？
	> 1.defer（IE）。  
	> 2.async（HTML5属性）。  
	> 3.创建script，插入DOM中，加载完毕后callBack。

* documen.write和 innerHTML的区别?  
	> document.write是直接将内容写入页面的内容刘，**会导致页面全部重绘**，innerHTML将内容写入某个DOM节点，**不会导致页面全部重绘**

* DOM操作——怎样添加、移除、移动、复制、创建和查找节点?
	> createDocumentFragment();  
	> createElement();  
	> createTextDode();  
	> appendChild();  
	> removeChild().
	> getElementById() 和 getElementsByTagName()

* .call() 和 .apply() 的含义和区别？
	> 这两个方法是属于function.prototype的方法属性。两个函数的目的都是为了借用别人的方法来调用,就像调用自己的一样。二者唯一的区别是调用方法格式不一样。  
	>   
	`fun.call(this,a,b,c,d)`  
	(this为当前对象，是未包含当前fun函数的对象，如此调用之后，this所指对象即拥有了fun函数，a,b,c,d是固有的属性)；  
	>
	而apply（）函数则是`fun.apply(this,args)`  
	(this的含义是相同的，关键是第二个参数args，这个是函数的固有属性，用来存放参数)。  
	>
	由此可见**apply（）用于函数参数不确定**的情况下使用。注意，this可替换成别的具体对象。

* 数组和对象有哪些原生方法，列举一下？
	>LIFO 对应的push（）和pull（）；  
	FIFO对应的shift（）和pop（）。  
	重排序reverse（）和sort（）。toString（）。  
	改变原数组的方法：pop()、push()、reverse()、shift()、sort()、splice()、unshift()；  
	不改变原数组的方法：concat()、join()、slice()、toString()。

* JS 怎么实现一个类。怎么实例化这个类
	> (1)构造函数方法： function className（）{}，通过关键字new 来实例化  
	> (2)object.create方法
 

* JavaScript中的作用域与变量声明提升？

* 如何编写高性能的Javascript？

* 那些操作会造成内存泄漏？
	> 闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

* JQuery的源码看过吗？能不能简单概况一下它的实现原理？

* jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？
	> 返回的this就是jQuery.fn的实例.
	> 当你使用$()之后，实际是调用了`new jQuery.fn.init( selector, context )`。
	> jQuery.fn的类体声明如下：  
	>  
	>    
    	jQuery.fn = jQuery.prototype = {
			// The current version of jQuery being used
			jquery: version,
			constructor: jQuery,
			// Start with an empty selector
			selector: "",  
			// The default length of a jQuery object is 0
			length: 0,
			toArray: function() {
			return slice.call( this );
			},
		......


* jquery中如何将数组转化为json字符串，然后再转化回来？

* jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？

* jquery.extend 与 jquery.fn.extend的区别？
	>jQuery.extend(): 把两个或者更多的对象合并到第一个当中。  
	扩展静态方法；jQuery.fn.extend():把对象挂载到jQuery的prototype属性，来扩展一个新的jQuery实例方法。  
	扩展实例方法；jQuery.extend()是直接用$调用，jQuery.fn.extend()是用$()调用，另外jQuery.extend()接收多个对象作为参数，如果只有一个参数，则把这个对象的属性方法附加到jQuery上，如果含有多个参数，则把后面的对象的属性和方法附加到第一个对象上

* jQuery 的队列是如何实现的？队列可以用在哪些地方？
  > jQuery核心中, 有一组队列控制方法, 这组方法由queue()/dequeue()/clearQueue()三个方法组成, 它对需要连续按序执行的函数的控制可以说是简明自如, 主要应用于animate ()方法, ajax以及其他要按时间顺序执行的事件中

* 谈一下Jquery中的bind(),live(),delegate(),on()的区别？
  > bind(type,[data],fn) 为每个匹配元素的特定事件绑定事件处理函数  
  >`$("a").bind("click",function(){alert("ok");});`  

  >live(type,[data],fn) 给所有匹配的元素附加一个事件处理函数，即使这个元素是以后再添加进来的    
  >`$("a").live("click",function(){alert("ok");});`    

  >delegate(selector,[type],[data],fn) 指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的  函数     
  >`$("#container").delegate("a","click",function(){alert("ok");})`    

  >`on(events,[selector],[data],fn)` 在选择元素上绑定一个或多个事件的事件处理函数    
  >差别：   
  >.bind()是直接绑定在元素上    
  >.live()则是通过冒泡的方式来绑定到元素上的。更适合列表类型的，绑定到document DOM节点上。和.bind()的优势是支持动态数据。   
  >.delegate()则是更精确的小范围使用事件代理，性能优于.live()     
  >.on()则是最新的1.9版本整合了之前的三种方式的新事件绑定机制     

* JQuery一个对象可以同时绑定多个事件，这是如何实现的？

* 是否知道自定义事件。jQuery里的fire函数是什么意思，什么时候用？

* jQuery 是通过哪个方法和 Sizzle 选择器结合的？（jQuery.fn.find()进入Sizzle）

* 针对 jQuery性能的优化方法？

* Jquery与jQuery UI有啥区别？

* JQuery的源码看过吗？能不能简单说一下它的实现原理？

* jquery 中如何将数组转化为json字符串，然后再转化回来？

* jQuery和Zepto的区别？各自的使用场景？

* 针对 jQuery 的优化方法？

* Zepto的点透问题如何解决？

* jQueryUI如何自定义组件?

* 需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？

* 如何判断当前脚本运行在浏览器还是node环境中？（阿里）

* 移动端最小触控区域是多大？

* jQuery 的 slideUp动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?

* 把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？

* 移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？（click 有 300ms 延迟,为了实现safari的双击事件的设计，浏览器要知道你是不是要双击操作。）

* 知道各种JS框架(Angular, Backbone, Ember, React, Meteor, Knockout...)么? 能讲出他们各自的优点和缺点么?

* Underscore 对哪些 JS 原生对象进行了扩展以及提供了哪些好用的函数方法？

* 解释JavaScript中的作用域与变量声明提升？

* 那些操作会造成内存泄漏？

* JQuery一个对象可以同时绑定多个事件，这是如何实现的？

* Node.js的适用场景？

* (如果会用node)知道route, middleware, cluster, nodemon, pm2, server-side rendering么?

* 解释一下 Backbone 的 MVC 实现方式？

* 什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?

* 知道什么是webkit么? 知道怎么用浏览器的各种工具来调试和debug代码么?

* 如何测试前端代码么? 知道BDD, TDD, Unit Test么? 知道怎么测试你的前端工程么(mocha, sinon, jasmin, qUnit..)?

* 前端templating(Mustache, underscore, handlebars)是干嘛的, 怎么用?

* 简述一下 Handlebars 的基本用法？

* 简述一下 Handlerbars 的对模板的基本处理流程， 如何编译的？如何缓存的？

* 用js实现千位分隔符?(来源：前端农民工，提示：正则+replace)

* 检测浏览器版本版本有哪些方式？

* 我们给一个dom同时绑定两个点击事件，一个用捕获，一个用冒泡，你来说下会执行几次事件，然后会先执行冒泡还是捕获  

<a name="css"></a>
# CSS部分

* 介绍一下标准的CSS的盒子模型？与低版本IE的盒子模型有什么不同的？

* CSS选择符有哪些？哪些属性可以继承？

* CSS优先级算法如何计算？

* CSS3新增伪类有那些？

* 如何居中div？如何居中一个浮动元素？如何让绝对定位的div居中？

* display有哪些值？说明他们的作用。

* position的值relative和absolute定位原点是？

* CSS3有哪些新特性？

* 请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

* 用纯CSS创建一个三角形的原理是什么？

* 一个满屏 品 字布局 如何设计?

* 常见兼容性问题？

* li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？

* 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？

* 为什么要初始化CSS样式。

* absolute的containing block计算方式跟正常流有什么不同？

* CSS里的visibility属性有个collapse属性值是干嘛用的？在不同浏览器下以后什么区别？

* position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

* 对BFC规范(块级格式化上下文：block formatting context)的理解？

* CSS权重优先级是如何计算的？

* 请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式

* 移动端的布局用过媒体查询吗？

* 使用 CSS 预处理器吗？喜欢那个？

* CSS优化、提高性能的方法有哪些？

* 浏览器是怎样解析CSS选择器的？

* 在网页中的应该使用奇数还是偶数的字体？为什么呢？

* margin和padding分别适合什么场景使用？

* 抽离样式模块怎么写，说出思路，有无实践经验？[阿里航旅的面试题]

* 元素竖向的百分比设定是相对于容器的高度吗？

* 全屏滚动的原理是什么？用到了CSS的那些属性？

* 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？

* 视差滚动效果，如何给每页做不同的动画？（回到顶部，向下滑动要再次出现，和只出现一次分别怎么做？）

* ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。

* 如何修改chrome记住密码后自动填充表单的黄色背景 ？

* 你对line-height是如何理解的？

* 设置元素浮动后，该元素的display值是多少？（自动变成display:block）

* 怎么让Chrome支持小于12px 的文字？

* 让页面里的字体变清晰，变细用CSS怎么做？（-webkit-font-smoothing: antialiased;）

* font-style属性可以让它赋值为“oblique” oblique是什么意思？

* position:fixed;在android下无效怎么处理？

* 如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）

* display:inline-block 什么时候会显示间隙？(携程)

* overflow: scroll时不能平滑滚动的问题怎么处理？

* 有一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度。

* png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？

* 什么是Cookie 隔离？（或者说：请求资源的时候不要让它带cookie怎么做）

* style标签写在body后与body前有什么区别？

<a name="HTML"></a>
# HTML部分  

* Doctype作用？严格模式与混杂模式如何区分？它们有何意义?

* HTML5 为什么只需要写 <!DOCTYPE HTML>？

* 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

* 页面导入样式时，使用link和@import有什么区别？

* 介绍一下你对浏览器内核的理解？

* 常见的浏览器内核有哪些？

* html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

* 简述一下你对HTML语义化的理解？

* HTML5的离线储存怎么使用，工作原理能不能解释一下？

* 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

* 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

* iframe有那些缺点？

* Label的作用是什么？是怎么用的？（加 for 或 包裹）

* HTML5的form如何关闭自动完成功能？

* 如何实现浏览器内多个标签页之间的通信? (阿里)

* webSocket如何兼容低浏览器？(阿里)

* 页面可见性（Page Visibility）API 可以有哪些用途？

* 如何在页面上实现一个圆形的可点击区域？

* 实现不使用 border 画出1px高的线，在不同浏览器的Quirksmode和CSSCompat模式下都能保持同一效果。

* 网页验证码是干嘛的，是为了解决什么安全问题？

* tite与h1的区别、b与strong的区别、i与em的区别？