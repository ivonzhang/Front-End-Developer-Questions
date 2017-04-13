# Welcome to the Front-End-Developer-Questions wiki!

# 目录
* 1. [**JavaScript部分**](#JavaScript)
* 2. [**
* **](#css) 
* 3. [**HTML部分**](#HTML) 
* 4. [**Nodejs部分**](#NODEJS) 

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
	> 1.对象字面量的方式p＝｛｝；2.用function来模拟无参的构造函数，再定义属性；3.用function模拟构造函数，利用this；4.利用工厂方式（内置对象Object）；5.利用原型方式来创建；6.混合方式来创建。  

* Q6：Javascript作用链域?
	> 当代码在一个环境中执行时，会创建变量对象的一个作用域链。如果是个函数，则将其活动对象作为变量对象。活动对象在最开始只包含一个arguments对象。而下一个变量对象则来自下一个包含环境。如此一直延续到全局执行环境，这种组织形式即为作用域链。内部函数可访问外部变量，外部变量无法访问内部函数。注意：js没有块级作用域，若要形成块级作用域，可通过`（function（）｛｝）（）`；立即执行的形式实现。

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
	> [1,NAN,NAN]

* Q12：什么是闭包（closure），为什么要用它？
	> 闭包指的是一个函数可以访问另一个函数作用域中变量的函数。常见的构造方法，是在一个函数内部定义另外一个函数。内部函数可以引用外层的参数和变量；参数和变量不会被垃圾回收机制回收。注意，闭包的原理是作用域链，所以闭包访问的上级作用域中的变量是个对象，其值为其运算结束后的最后一个值。除非用立即执行函数来解决。    
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
	> (1)不要在同一行声明多个变量。

  	> (2)请使用 ===/!==来比较true/false或者数值

  	> (3)使用对象字面量替代new Array这种形式

  	> (4)不要使用全局函数。

  	> (5)Switch语句必须带有default分支

  	> (6)函数不应该有时候有返回值，有时候没有返回值。

  	> (7)For循环必须使用大括号

  	> (8)If语句必须使用大括号

  	> (9)for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。


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

	> 使用**extend**来继承:

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
	> jQuery.extend(): 把两个或者更多的对象合并到第一个当中。  
	扩展静态方法；jQuery.fn.extend():把对象挂载到jQuery的prototype属性，来扩展一个新的jQuery实例方法。  
	扩展实例方法；jQuery.extend()是直接用$调用，jQuery.fn.extend()是用$()调用，另外jQuery.extend()接收多个对象作为参数，如果只有一个参数，则把这个对象的属性方法附加到jQuery上，如果含有多个参数，则把后面的对象的属性和方法附加到第一个对象上

* jQuery 的队列是如何实现的？队列可以用在哪些地方？
	> jQuery核心中, 有一组队列控制方法, 这组方法由queue()/dequeue()/clearQueue()三个方法组成, 它对需要连续按序执行的函数的控制可以说是简明自如, 主要应用于animate ()方法, ajax以及其他要按时间顺序执行的事件中

* 谈一下Jquery中的bind(),live(),delegate(),on()的区别？  
  	> bind(type,[data],fn) 为每个匹配元素的特定事件绑定事件处理函数  
  	>`$("a").bind("click",function(){alert("ok");});`  

  	> live(type,[data],fn) 给所有匹配的元素附加一个事件处理函数，即使这个元素是以后再添加进来的    
  	>`$("a").live("click",function(){alert("ok");});`    

  	> delegate(selector,[type],[data],fn) 指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的  函数     
  	>`$("#container").delegate("a","click",function(){alert("ok");})`    

  	>`on(events,[selector],[data],fn)` 在选择元素上绑定一个或多个事件的事件处理函数    
  	> 差别：   
  	> .bind()是直接绑定在元素上    
  	> .live()则是通过冒泡的方式来绑定到元素上的。更适合列表类型的，绑定到document DOM节点上。和.bind()的优势是支持动态数据。   
  	> .delegate()则是更精确的小范围使用事件代理，性能优于.live()     
  	> .on()则是最新的1.9版本整合了之前的三种方式的新事件绑定机制     

* JQuery一个对象可以同时绑定多个事件，这是如何实现的？

* 是否知道自定义事件。jQuery里的fire函数是什么意思，什么时候用？
	> jQuery的事件自定义事件还是通过on绑定的，然后再通过trigger来触发这个事件,如下：  
	>
		   //给element绑定hello事件
			element.bind("hello",function(){
			alert("hello world!");
			});
			//触发hello事件
			element.trigger("hello");  
	
	> 例子中就自定义了一个hello事件，通过trigger来触发，还可以传递参数，`trigger(tpye[,datea])`方法有两个参数，第一个参数是要触发的事件类型，第二个单数是要传递给事件处理函数的附加数据，以数组形式传递。

* jQuery 是通过哪个方法和 Sizzle 选择器结合的？
	>当$函数的参数类型为string时，jQuery.fn.find()进入Sizzle

* 针对 jQuery性能的优化方法？   
	* 总是从ID选择器开始继承
	* 在class前使用tag(标签名)  
	* 将jQuery对象缓存起来，即先通过选择器找出jQuery对象赋值给一个变量，然后利用已赋值的变量进行各种绑定和操作，.click, .css 等等  
	* 对直接的DOM操作进行限制,这里的基本思想是在内存中建立你确实想要的东西，然后更新DOM。直接操作dom太慢了。  
	* 除非在特殊情况下, 否则每一个js事件(例如:click, mouseover等.)都会冒泡到父级节点。当我们需要给多个元素调用同个函数时这点会很有用。代替这种效率很差的多元素事件监听的方法就是, 你只需向它们的父节点绑定一次。  
	* 推迟到 $(window).load  
	* 压缩JavaScript  
	* 尽量使用ID代替Class
	* 给选择器一个上下文,jQuery( expression, context ),如：`$('.myDiv' , $("#listItem") )`在列表#listItem中寻找.myDiv
	* 慎用 .live()方法（应该说尽量不要使用）  
>


* Jquery与jQuery UI有啥区别？
	* jQuery是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。

	* jQuery UI则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等

* JQuery的源码看过吗？能不能简单说一下它的实现原理？

* jquery中如何将数组转化为json字符串，然后再转化回来？
	> jquery中没有这样将数组直接转换为json字符串的方法。但可以通过扩展来实现：
	> 
		$.fn.stringifyArray = function(array) {
			return JSON.stringify(array)
		}
		$.fn.parseArray = function(array) {
			return JSON.parse(array)
		}

    > 然后调用：
    `$("").stringifyArray(array)`


* jQuery和Zepto的区别？各自的使用场景？

* 针对 jQuery 的优化方法？
	* 基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。

	* 频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。
比如：var str=$("a").attr("href");

	* for (var i = size; i < arr.length; i++) {}
 for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：
 `for (var i = size, length = arr.length; i < length; i++) {}`

* Zepto的点透问题如何解决？

* jQueryUI如何自定义组件?

* 需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？

* 如何判断当前脚本运行在浏览器还是node环境中？（阿里）

* 移动端最小触控区域是多大？
	> 44*44?

* jQuery 的 slideUp动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?
	> 网上找到的，没试过，不知道对不对？  
	> 1、在触发元素上的事件设置为延迟处理, 即可避免滞后反复执行的问题（使用setTimeout）  
	> 
	> 2、在触发元素的事件时预先停止所有的动画，再执行相应的动画事件（使用stop） 
	>  
	>     $("#div").stop();//停止当前动画，继续下一个动画 
    	$("#div").stop(true);//清除元素的所有动画 
    	$("#div").stop(false, true);//让当前动画直接到达末状态 ，继续下一个动画
    	$("#div").stop(true, true);//清除元素的所有动画，让当前动画直接到达末状态  

	> 这里推荐使用第二种方法：  
	`$("#div").stop().animate({width:"100px"},100); ` 


* 把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？

* 移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？  
	> click 有 300ms 延迟,为了实现safari的双击事件的设计，浏览器要知道你是不是要双击操作。  
	> 
	> 300ms。因为浏览器想看看你是不是要进行双击（double tap）操作。引入插件fastclick.js可以解决，Chrome浏览器在安卓设备上的时候，设置meta头信息中 user-scalable=no 但是这样就无法让用户多点触控缩放网页了。

* 知道各种JS框架(Angular, Backbone, Ember, React, Meteor, Knockout...)么? 能讲出他们各自的优点和缺点么?

* Underscore 对哪些 JS 原生对象进行了扩展以及提供了哪些好用的函数方法？

* 解释JavaScript中的作用域与变量声明提升？

* 那些操作会造成内存泄漏？
	> 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。

	> setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
**控制台日志、循环**（在两个对象彼此引用且彼此保留时，就会产生一个循环）。闭包并不会引起内存泄漏，只是由于IE9 之前的版本对JScript对象和COM对象使用不同的垃圾收集，从而导致内存无法进行回收。

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
  
	     function commafy(num) {  
			 num = num + '';  
			 var reg = /(-?d+)(d{3})/;  
			 if(reg.test(num)){  
			  num = num.replace(reg, '$1,$2');  
			 }  
			 return num;  
		}  

* 检测浏览器版本版本有哪些方式？  
	> 功能检测、userAgent特征检测  
	> 
	比如：navigator.userAgent
	//"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36
	  (KHTML, like Gecko) Chrome/41.0.2272.101 Safari/537.36"

* 我们给一个dom同时绑定两个点击事件，一个用捕获，一个用冒泡，你来说下会执行几次事件，然后会先执行冒泡还是捕获  

* js中的变量提升？  
	* 理解这个，首先要理解**作用域**，在此不做详述。  
	* 在javascript，变量有4种基本方式进入作用域：  
	1 语言内置：所有的作用域里都有this和arguments；(译者注：经过测试arguments在全局作用域是不可见的)  
	2 形式参数：函数的形式参数会作为函数体作用域的一部分；  
	3 函数声明：像这种形式：function foo(){}；  
	4 变量声明：像这样：var foo；  
	理解变量提升：**函数声明和变量声明总是会被解释器悄悄地被“提升”到方法体的最顶部**，而**赋值**在后，如： 
 
			function foo() {  
				bar();  
				var x = 1;  
			}   
	  
		实际上被解析为：  

		    function foo() {  
				var x;  
				bar();  
				x = 1;  
			}  

<a name="css"></a> 

* xss，csrf的概念以及防范方法  
	详情请看[XSS攻击及防御](http://blog.csdn.net/ghsau/article/details/17027893)，[CSRF攻击](http://www.cnblogs.com/hyddd/archive/2009/04/09/1432744.html) 

* CommonJs，AMD，CMD规范  
	[参考CommonJS，AMD，CMD](https://zhuanlan.zhihu.com/p/22954387)  

* 谈谈你对前端模块化的理解  
	前端模块话就是把复杂的文件分成一个个独立的模块，比如js文件，分成独立的模块之后有利于代码的重用和维护，但是这样又会引来模块与模块之间的依赖问题，所以就有了CommonJS、AMD、CMD规范，最后出现了webpack，webpack就是前端模块话的一种解决方案，基本上大公司都会使用webpack，想要详细的学习webpack的话请看[webpack简明使用教程](https://zhuanlan.zhihu.com/p/23538138)  

* 优雅降级和渐进增强  
	优雅降级指的是一开始就构建功能完好的网站，然后在慢慢兼容低版本的浏览器，使得各个浏览器之间的差异不要太大。  
	渐进增强是指在基本功能得到满足的情况下，对支持新特性的浏览器使用新特性，带给用户更换的体验。  
	优雅降级和渐进增强的出发点不同，前者是慢慢向下兼容，是向后看，后着是慢慢向上，增强功能，是向前看。  

* 前端优化（提高网页的加载速度）   
	1、使用css sprites，可以有效的减少http请求数    
	2、使用缓存      
	3、压缩js，css文件，减小文件体积      
	4、使用cdn，减小服务器负担      
	5、懒加载图片  
	6、预加载css，js文件      
	7、避免dom结构的深层次嵌套      
	8、给DOM元素添加样式时，把样式放到类中，直接给元素添加类，减少重构，回流  
	[雅虎前端优化35条黄金定律](http://www.cnblogs.com/lei2007/archive/2013/08/16/3262897.html)  

* H5标签语义化
	标签语义化，比如header，footer，nav，aside，article，section等，新增了很多表单元素，入email，url等，除去了center等样式标签，还有除去了有性能问题的frame，frameset等标签。  
	html5的语义化指的是用正确的标签包含正确的内容，比如nav标签，里面就应该包含导航条的内容，而不是用做其他的用途，标签语义化的好处就是结构良好，便于阅读，方便威化，也有利于爬虫的查找，提高搜索率。  

* 事件委托是什么  
	让利用事件冒泡的原理，让自己的所触发的事件，让他的父元素代替执行！  

* ”==”和“===”的不同  
	前者会自动转换类型；后者不会。  

* 介绍一下 JS 有哪些内置对象  
	- Object对象  
	- 数据类型对象：Boolean、String、Number、Array  
	- 其他对象：Function、Argument、Math、Date、RegExp、Error   


* 写出程序运行的结果?  
* 
	    for(var i=0, j=0; i<10, j<6; i++, j++){
      		k = i + j;
    	}
    	//浏览器输出： 10
	此时，`i=6，j=6` 因为循环体重的逻辑判断 `i<10, j<6` 是逗号表达式，以最终的`j<6`的返回值为基准，所以退出循环前 i和j都等于5，故`k=5+5`，结果为10 。此时，若交换为`j<6, i<10`，输出的k值则是18 。  

* 如何控制alert中的换行？  
	`alert("first line\n second line")`  









# CSS部分

* 介绍一下标准的CSS的盒子模型？与低版本IE的盒子模型有什么不同的？
	> （1）有两种， IE 盒子模型、W3C 盒子模型；  
（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；  
（3）区  别： IE的content部分把 border 和 padding计算了进去;

* CSS选择符有哪些？哪些属性可以继承？  
	* 1.id选择器（ # myid）  
    2.类选择器（.myclassname）  
    3.标签选择器（div, h1, p）  
    4.相邻选择器（h1 + p）  
    5.子选择器（ul > li）  
    6.后代选择器（li a）  
    7.通配符选择器（ * ）  
    8.属性选择器（a[rel = "external"]）  
    9.伪类选择器（a:hover, li:nth-child）  

	* 可继承的样式： font-size font-family color, UL LI DL DD DT;

	* 不可继承的样式：border padding margin width height ;

* CSS优先级算法如何计算？
	* 优先级就近原则，同权重情况下样式定义最近者为准;

	* 载入样式以最后载入的定位为准;

	> 优先级为:  
   !important >  id > class > tag  
    **important 比 内联优先级高**

* CSS3新增伪类有那些？
	> 举例：  
    **p:first-of-type** 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。  
    **p:last-of-type**  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。  
    **p:only-of-type**  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。  
    p:only-child        选择属于其父元素的唯一子元素的每个 <p> 元素。  
    **p:nth-child(2)**  选择属于其父元素的第二个子元素的每个 <p> 元素。  

    > **:after**          在元素之前添加内容,也可以用来做清除浮动。  
    **:before**         在元素之后添加内容  
    :enabled           
    :disabled       控制表单控件的禁用状态。  
    :checked        单选框或复选框被选中。  

* 如何居中div？如何居中一个浮动元素？如何让绝对定位的div居中？
	* 水平居中：给div设置一个宽度，然后添加margin:0 auto属性

		    div{
		    	width:200px;
		    	margin:0 auto;
	    	 }
	* 让绝对定位的div居中

			div {
				position: absolute;
				width: 300px;
				height: 300px
				margin: auto;
				top: 0;
				left: 0;
				bottom: 0;
				right: 0;
				background-color: pink; /* 方便看效果 */
			}  
	* 水平垂直居中一

		确定容器的宽高 宽500 高 300 的层设置层的外边距  

			div {
				position: relative; /* 相对定位或绝对定位均可 */
				width:500px; 
				height:300px;
				top: 50%;
				left: 50%;
				margin: -150px 0 0 -250px;  /* 外边距为自身宽高的一半 */
				background-color: pink; /* 方便看效果 */
			
			 }  
	* 水平垂直居中二

		未知容器的宽高，利用 `transform` 属性

			div {
				position: absolute; /* 相对定位或绝对定位均可 */
				width:500px; 
				height:300px;
				top: 50%;
				left: 50%;
				transform: translate(-50%, -50%);
				background-color: pink; /* 方便看效果 */
			
			}  
	* 水平垂直居中三

		利用 flex 布局实际使用时应考虑兼容性

			.container {
			    display: flex; 
			    align-items: center;        /* 垂直居中 */
			    justify-content: center;    /* 水平居中 */
			
			}
			.container div {
			    width: 100px;
			    height: 100px;
			    background-color: pink;     /* 方便看效果 */
			}  

* display有哪些值？说明他们的作用。
	> block         块类型。默认宽度为父元素宽度，可设置宽高，换行显示。  
  	none          缺省值。象行内元素类型一样显示。  
  inline        行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。  
  inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。  
  list-item     象块类型元素一样显示，并添加样式列表标记。  
  table         此元素会作为块级表格来显示。   
  inherit       规定应该从父元素继承 display 属性的值。  

* position的值relative和absolute定位原点是？
*	> **absolute**
    生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。  
  **fixed** （老IE不支持）
    生成绝对定位的元素，相对于浏览器窗口进行定位。  
  **relative**
    生成相对定位的元素，相对于其正常位置进行定位。  
  **static**
    默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。  
  **inherit**
    规定从父元素继承 position 属性的值。  

* CSS3有哪些新特性？
	> 新增各种CSS选择器  （: not(.input)：所有 class 不是“input”的节点）  
  圆角           （border-radius:8px）  
  多列布局        （multi-column layout）  
  阴影和反射        （box-hadow\box-reflect）  
  文字特效      （text-shadow）  
  文字渲染      （text-decoration）  
  线性渐变      （gradient）  
  旋转          （transform）
  增加了旋转,缩放,定位,倾斜,动画，多背景
  `transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:`

* 请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

* 用纯CSS创建一个三角形的原理是什么？
	> 把上、左、右三条边隐藏掉（颜色设为 transparent）  
	> 
	    #demo {
	      width: 0;
	      height: 0;
	      border-width: 20px;
	      border-style: solid;
	      border-color: transparent transparent red transparent;
	    }

* 一个满屏 品 字布局 如何设计?
	> 简单的方式：  
    上面的div宽100%，  
    下面的两个div分别宽50%，  
    然后用float或者inline使其不换行即可

* 常见兼容性问题？

* li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
	> 行框的排列会受到中间空白（回车\空格）等的影响，因为空格也属于字符,这些空白也会被应用样式，占据空间，所以会有间隔，把字符大小设为0，就没有空格了。

* 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？
	* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.

	* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。

	* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。

  浮动ie产生的双倍距离 `#box{ float:left; width:10px; margin:0 0 0 100px;}`

  这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)

  渐进识别的方式，从总体中逐渐排除局部。

  首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
  接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。

  css  

	  .bb{
		  background-color:#f1ee18;/*所有识别*/
		  .background-color:#00deff\9; /*IE6、7、8识别*/
		  +background-color:#a200ff;/*IE6、7识别*/
		  _background-color:#1e0bd1;/*IE6识别*/
	  }  

IE下,可以使用获取常规属性的方法来获取自定义属性,
	   也可以使用getAttribute()获取自定义属性;
	   Firefox下,只能使用getAttribute()获取自定义属性。
   解决方法:统一通过getAttribute()获取自定义属性。  
	
 IE下,even对象有x,y属性,但是没有pageX,pageY属性;
   Firefox下,event对象有pageX,pageY属性,但是没有x,y属性。
 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
   可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。

超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}

* 为什么要初始化CSS样式。
	* 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

	* 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

	最简单的初始化方法： `* {padding: 0; margin: 0;} （强烈不建议）`

	淘宝的样式初始化代码：  

	    body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
    	body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
    	h1, h2, h3, h4, h5, h6{ font-size:100%; }
    	address, cite, dfn, em, var { font-style:normal; }
    	code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
    	small{ font-size:12px; }
    	ul, ol { list-style:none; }
    	a { text-decoration:none; }
    	a:hover { text-decoration:underline; }
    	sup { vertical-align:text-top; }
    	sub{ vertical-align:text-bottom; }
    	legend { color:#000; }
    	fieldset, img { border:0; }
    	button, input, select, textarea { font-size:100%; }
    	table { border-collapse:collapse; border-spacing:0; } 

* absolute的containing block计算方式跟正常流有什么不同？
	> 无论属于哪种，都要先找到其祖先元素中最近的 position 值不为 static 的元素，然后再判断：  
		1、若此元素为 inline 元素，则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；  
		2、否则,则由这个祖先元素的 padding box 构成。
		如果都找不到，则为 initial containing block。  

	> 补充：  
		1. static(默认的)/relative：简单说就是它的父元素的内容框（即去掉padding的部分）  
		2. absolute: 向上找最近的定位为absolute/relative的元素  
		3. fixed: 它的containing block一律为根元素(html/body)，根元素也是initial containing block

* CSS里的visibility属性有个collapse属性值是干嘛用的？在不同浏览器下以后什么区别？

* position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

* 对BFC规范(块级格式化上下文：block formatting context)的理解？

* **CSS权重优先级是如何计算的**？
	> 以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：  
	> 
	    /*权重为1*/
	    div{
	    }
	    /*权重为10*/
	    .class1{
	    }
	    /*权重为100*/
	    #id1{
	    }
	    /*权重为100+1=101*/
	    #id1 div{
	    }
	    /*权重为10+1=11*/
	    .class1 div{
	    }
	    /*权重为10+10+1=21*/
	    .class1 .class2 div{
	    }  
	> **如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现**
    
* 请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式

* 移动端的布局用过媒体查询吗？

* 使用 CSS 预处理器吗？喜欢那个？
	> SASS (SASS、LESS没有本质区别，只因为团队
	> 前端都是用的SASS)

* CSS优化、提高性能的方法有哪些？

* 浏览器是怎样解析CSS选择器的？

* 在网页中的应该使用奇数还是偶数的字体？为什么呢？

* margin和padding分别适合什么场景使用？

* 抽离样式
* 模块怎么写，说出思路，有无实践经验？[阿里航旅的面试题]

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
	> 多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms

* display:inline-block 什么时候会显示间隙？(携程)
	> 移除空格、使用margin负值、使用font-size:0、letter-spacing、word-spacing

* overflow: scroll时不能平滑滚动的问题怎么处理？

* 有一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度。

* png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？

* 什么是Cookie 隔离？（或者说：请求资源的时候不要让它带cookie怎么做）
	> 如果静态文件都放在主域名下，那静态文件请求的时候都带有的cookie的数据提交给server的，非常浪费流量，
所以不如隔离开。  

	> 因为cookie有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有cookie数据，
这样可以降低请求头的大小，降低请求时间，从而达到降低整体请求延时的目的。

	>　同时这种方式不会将cookie传入Web Server，也减少了Web Server对cookie的处理分析环节，
提高了webserver的http请求的解析速度。

* style标签写在body后与body前有什么区别？

<a name="HTML"></a>
# HTML部分  

* Doctype作用？严格模式与混杂模式如何区分？它们有何意义?
	> (1）<!DOCTYPE>声明位于位于HTML文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。  
	> 
	(2）标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

* ##### HTML5 为什么只需要写 <!DOCTYPE HTML>？
	###### HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

* 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？
	> 首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。  
	> 
	（1）行内元素有：a b span img input select strong（强调的语气）  
	（2）块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p    
	（3）常见的空元素：`<br> <hr> <img> <input> <link> <meta>`  
    		鲜为人知的是：`<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>`

* 页面导入样式时，使用link和@import有什么区别？
	* （1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;   
	   
	* （2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;

	* （3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;

* 介绍一下你对浏览器内核的理解？
	> 主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。  
	> 
	渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。  

	> JS引擎则：解析和执行javascript来实现网页的动态效果。  
	> 
	> 最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

* 常见的浏览器内核有哪些？
	* Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
	* Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
	* Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]
	* Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]

* html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？
	* HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。   
      绘画 canvas;  
      用于媒介回放的 video 和 audio 元素;  
      本地离线存储 **localStorage** 长期存储数据，浏览器关闭后数据不丢失;  
      **sessionStorage** 的数据在浏览器关闭后自动删除;  
      语意化更好的内容元素，比如 article、footer、header、nav、section;  
      表单控件，calendar、date、time、email、url、search;  
      新的技术webworker, websocket, Geolocation;    

		移除的元素：
		      纯表现的元素：basefont，big，center，font, s，strike，tt，u;  
		      对可用性产生负面影响的元素：frame，frameset，noframes；

	* 支持HTML5新标签：
	     IE8/IE7/IE6支持通过document.createElement方法产生的标签，
	     可以利用这一特性让这些浏览器支持HTML5新标签，
	     浏览器支持新标签后，还需要添加标签默认的样式。
	
	     当然也可以直接使用成熟的框架、比如html5shim;  
	 ```<!--[if lt IE 9]>  
		<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>  
	 <![endif]-->```

	* 如何区分HTML5： DOCTYPE声明\新增的结构元素\功能元素

* 简述一下你对HTML语义化的理解？
	用正确的标签做正确的事情。
	html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
	即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
	搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

* HTML5的离线储存怎么使用，工作原理能不能解释一下？
	>  在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。  
	原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。  

	> 如何使用：
	1、页面头部像下面一样加入一个manifest的属性；  
	2、在cache.manifest文件的编写离线存储的资源，写法如下：
  	>
	    CACHE MANIFEST  
	    #v0.11  
	    CACHE:  
	    js/app.js  
	    css/style.css  
	    NETWORK:  
	    resourse/logo.png  
	    FALLBACK:  
	    / /offline.html   

	> 3、在离线状态时，操作window.applicationCache进行需求实现。  
	详细的使用请参考：[有趣的HTML5：离线存储](https://segmentfault.com/a/1190000000732617)貌似这方案已经失效了？？？

* 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？
	> 在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。离线的情况下，浏览器就直接使用离线存储的资源。

* 请描述一下 cookies，sessionStorage 和 localStorage 的区别？
	 cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。  
	cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。  
	sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

	存储大小：  
	    cookie数据大小不能超过4k。  
	    sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
	
	有期时间：  
		localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；  
		sessionStorage  数据在当前浏览器窗口关闭后自动删除。  
		cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

* iframe有那些缺点？
	* iframe会阻塞主页面的Onload事件；
	* 搜索引擎的检索程序无法解读这种页面，不利于SEO;

	* iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。

		使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
		动态给iframe添加src属性值，这样可以绕开以上两个问题。

* Label的作用是什么？是怎么用的？（加 for 或 包裹）  
	 label标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。  

		<label for="Name">Number:</label>
		<input type=“text“name="Name" id="Name"/>
		
		<label>Date:<input type="text" name="B"/></label>

* HTML5的form如何关闭自动完成功能?  
	> 给不想要提示的 form 或某个 input 设置为 autocomplete=off。

* 如何实现浏览器内多个标签页之间的通信? (阿里)
	> WebSocket、SharedWorker；  
也可以调用localstorge、cookies等本地存储方式；

	> localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
	我们通过监听事件，控制它的值来进行页面信息通信；
	注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；

* webSocket如何兼容低浏览器？(阿里)
	> Adobe Flash Socket 、  
	ActiveX HTMLFile (IE) 、  
	基于 multipart 编码发送 XHR 、  
	基于长轮询的 XHR

* 页面可见性（Page Visibility）API 可以有哪些用途？
	> 通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;
	在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放；

* 如何在页面上实现一个圆形的可点击区域？
	> 1、map+area或者svg  
	2、border-radius  
	3、纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等

* 实现不使用 border 画出1px高的线，在不同浏览器的Quirksmode和CSSCompat模式下都能保持同一效果。
	`<div style="height:1px;overflow:hidden;background:red"></div>`

* 网页验证码是干嘛的，是为了解决什么安全问题？
	> 区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水；  
	有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试。

* tite与h1的区别、b与strong的区别、i与em的区别？
	> title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取也有很大的影响；  
	> 
	> strong是标明重点内容，有语气加强的含义，使用阅读设备阅读网络时：<strong>会重读，而<B>是展示强调内容。
	>
	i内容展示为斜体，em表示强调的文本；
	
	>Physical Style Elements -- 自然样式标签  
	b, i, u, s, pre  
	Semantic Style Elements -- 语义样式标签  
	strong, em, ins, del, code  
	应该准确使用语义样式标签, 但不能滥用, 如果不能确定时首选使用自然样式标签。

<a name="NODEJS"></a>
# Nodejs部分
* ### 如何更新npm的版本 ###
	* #### npm -g install npm@3.0.0 后面@跟的是版本号 ####
	* 更新node需要两步：  
		1）sudo npm install -g n   
		2）sudo n latest