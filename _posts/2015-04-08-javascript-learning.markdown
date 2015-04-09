---
layout: post
title: JavaScript学习笔记
category : 备忘
tagline: "备忘"
tags : [Web, JavaScript]
---

#javascript学习笔记

-----
###Value = undefined
在计算机程序中，经常会声明无值的变量。未使用值来声明的变量，其值实际上是 undefined。

在执行过以下语句后，变量 carname 的值将是 undefined：

    var carname;

包含undefined值的变量与尚未定义的变量是不一样的。如下面这个例子：

    var message; // 这个变量声明之后默认取得了undefined值

    // 下面这个变量并没有声明
    // varage

    alert(message); // "undefined"
    alert(age); // 产生错误

然后对未初始化的变量执行 typeof 操作符会返回 undefined 的值，而对未声明的变量执行 typeof 操作符同样也会返回 undefined 值。如下例子：

    var message; // 这个变量声明之后默认取得了undefined值

    // 下面这个变量并没有声明
    // varage

    alert(typeof message); // "undefined"
    alert(typeof age); // "undefined"

-----
###Null类型
从逻辑角度看，null 表示一个空对象指针，这也是使用 typeof 操作符检测 null 值会返回 "object" 的原因"。

    var car = null;
    alert(typeof car); // "object"

undefined 值派生自 null 值，因此 ECMA-262 规定对它们的相等性测试要返回 true。

    alert(null == undefined); // true
    alert(null === undefined); // false (因为它们是不同类型的值)

-----
###重新声明 JavaScript 变量
如果重新声明 JavaScript 变量，该变量的值不会丢失。

在以下两条语句执行后，变量 carname 的值依然是 "Volvo"：

    var carname="Volvo";
    var carname;

-----
###声明变量类型
当您声明新变量时，可以使用关键词 "new" 来声明其类型：

    var carname=new String;
    var x=      new Number;
    var y=      new Boolean;
    var cars=   new Array;
    var person= new Object;

JavaScript 变量均为对象。当您声明一个变量时，就创建了一个新的对象。

-----
###向未声明的 JavaScript 变量来分配值
如果您把值赋给尚未声明的变量，该变量将被自动作为全局变量声明。
这条语句：

    carname="Volvo";

将声明一个全局变量 carname，即使它在函数内执行。

-----
###对字符串和数字进行加法运算
请看这些例子：

    x=5+5;
    document.write(x);
 
    x="5"+"5";
    document.write(x);
 
    x=5+"5";
    document.write(x);
 
    x="5"+5;
    document.write(x);

结果是：

    10
    55
    55
    55

规则是：
如果把数字与字符串相加，结果将成为字符串。

-----
###NaN非数值
任何涉及NaN的操作都会返回NaN。NaN与任何值都不相等，包括NaN本身。

    alert(NaN == NaN); // false

isNaN() 判断参数是否 "不是数值"。isNaN() 在接收到一个值之后，会尝试将这个值转换为数值。某些不是数值的值会直接转换为数值。而不能被转换为数值的值都会导致这个函数返回true。

    alert(isNAN(NaN));    // true
    alert(isNAN(10));     // false (10 是一个数值)
    alert(isNAN("10"));   // false (可以被转换成数值10)
    alert(isNAN("blue")); // true (不能转换成数值)
    alert(isNAN(true));   // false (可以被转换成数值1)

-----
###*`<未解决>`* 循环引用问题
标记清除和引用计数的原理

目前JavaScript中的垃圾收集策略都是标记清除，因此不会产生循环引用问题。但是IE中有一部分对象并不是原生的JavaScript对象。参看《javascript高级程序设计第三版》 p79页：

>例如，其中BOM和DOM中的对象就是使用C++以COM (Component Object Model，组件对象模型)对象的形式实现的，而COM对象的垃圾收集机制采用的就是引用计数策略。因此，即使IE的javascript引擎是使用标记清除策略来实现的，但javascript访问的COM对象依然是基于引用计数策略的。换句话说，只要IE中设计COM对象，就会存在循环引用的问题。下面这个简单的例子，展示了使用COM对象导致的循环引用问题：

    var element = document.getElementById("some_element");
    var myObject = new Object();
    myObject.element = element;
    element.somObject = myObject;

[javascript垃圾收集机制与内存泄漏详解](http://www.cnblogs.com/adforce/archive/2012/12/04/2801200.html)

闭包引起的内存泄露

注：《javascript高级程序设计第三版》 p184

-----
###使用字面量方法和使用构造函数创建对象的区别

*1. 创建Object实例*

问题来源于《javascript高级程序设计第三版》 p84页的一句话：

>在通过字面量定义对象时，实际上不会调用Object的构造函数。

那么通过字面量定义对象和使用Object构造函数有什么区别呢？先看下面一个例子：

    var ObjectOld = Object;
    Object = function (){
        console.log("this is new Object");
    };

    var o1 = new Object();                      // this is new Object
    console.log(o1.constructor == Object);      // true
    console.log(o1.constructor == ObjectOld);   // false

    var o2 = {};                                // 没有输出
    console.log(o2.constructor == Object);      // false
    console.log(o2.constructor == ObjectOld);   // true

    var o3 = new ObjectOld();                   // 没有输出
    console.log(o3.constructor == Object);      // false
    console.log(o3.constructor == ObjectOld);   // true

    Object = ObjectOld;

实际上，上面所说的“不会调用Object的构造函数”的意思是没有使用全局变量Object引用的构造函数，也就是说并没有解析作用域。而显式地调用Object构造函数时，会在作用域链中顺序查找名为Object的构造函数。如果以同样的名字Object创建一个局部函数，所使用的构造函数会覆盖为该新创建的局部函数。否则，会顺序查找到最外层的全局Object函数。

再来看上面的例子，首先使用ObjectOld来引用原先的全局Object构造函数，再将Object变量引用为一个新的构造函数，该函数内执行打印“this is new Object”信息。三种情况分析如下：

- 使用显示调用构造函数时，在作用域链中查找到名为Object的函数，所以实际调用的是被覆盖的构造函数。
- 使用字面量定义对象时，并不会查找作用域链，而是直接调用原先的全局构造函数，所以并不会打印“this is new Object”信息。
- 使用显示调用ObjectOld引用的构造函数时，在作用域链中查找到的ObjectOld引用的就是原先的全局构造函数，因此打印结果和使用字面量时相同。

*2. 创建自定义对象的实例*

实际上，第一种情况是实例化了一个自定义对象，只是这个自定义对象的引用名为Object，而原先的全局构造函数Object使用了ObjectOld来引用。如果定义一个不太容易误解的构造函数，并实例化一个对象如下：

    function Persion(){
        this.name = "Tom";
        this.age = 23;
        this.getAge = function(){
            console.log(this.age);
        };
    }

    var p1 = new Persion();

实际上，我们可以将`var p1 = new Persion();`理解为如下四步：

    var p1  ={};
    p1.__proto__ = Persion.prototype;
    Persion.call(p1);
    return p1;

执行第三步`Persion.call(p1);`时，就会执行上文所说的在作用域链中顺序查找构造函数的过程。而理解其中第二步时，实际上标准javascript的对象是没有`__proto__`属性的，只要理解JavaScript对象内部存在指向构造函数原型的指针就可以了。

参考：

[js关于字面量与构造函数创建对象的几点理解](http://my.oschina.net/bothyan/blog/125668)
[深入理解js构造函数](http://www.2cto.com/kf/201402/281841.html)
[JavaScript类和继承：constructor属性](http://developer.51cto.com/art/200907/134913.htm)

-----
###默认的toString()方法
问题来源于如下的例子：

        var tem = new Object();
        alert(tem.toString()); // 结果是 [object Object] 为什么?

参考[微软的Web开发文档](https://msdn.microsoft.com/zh-cn/library/k6xhc6yc)

>toString 方法是一个所有内置的 JavaScript 对象的成员。 它的行为取决于对象的类型。

| Object | 行为 |
| :--- | :--- |
| 数组 | 将 Array 的元素转换为字符串。 结果字符串被连接起来，用逗号分隔。 |
| 布尔值 | 如果布尔值为 true，则返回“true”。 否则返回“false”。 |
| 日期 | 返回日期的文本表示形式。 |
| 错误 | 返回一个包含相关错误信息的字符串。 |
| 函数 | 返回如下格式的字符串，其中 functionname 是一个函数的名称，此函数的 toString 方法被调用：`function functionname( ) { [native code] }` |
| Number | 返回数字的文字表示形式。 |
| 字符串 | 返回 String 对象的值。 |
| 默认 | 返回 "[object objectname]"，其中 objectname 为对象类型的名称。 |

对应最后一条，因为tem的对象类型名称为 Object ，所以结果是`[object Object]`。如果我们定义一个Date类型的对象如下：

    var d = new Date()
    console.log(d.toString()); // Wed Apr 08 2015 18:39:53 GMT+0800 (中国标准时间)

我们发现结果并不是`[object Date]`，那是因为Date中继承于Object的toString方法已经被重新定义的toString方法覆盖了。我们要使用Object原型中的toString方法才行：

    var d = new Date()
    console.log(Object.prototype.toString.call(d)); //[object Date]

参考：
[如何获取一个js对象的类型名称](http://segmentfault.com/q/1010000000669230)

-----
###使用Date构造函数根据特定的日期和时间创建对象
使用Date.parse()方法、直接传入符合Date.parse()方法的表示日期的字符串、使用Date.UTC()方法：这三种方法传入的时间都是本地时间。而直接传入符合Date.UTC()方法的参数时，传入的是UTC时间。例子与结果如下：

        var  dd = new Date(Date.parse("2000-01-01T02:00:00"));
        output.innerText += dd.toString() + "\n";       // Sat Jan 01 2000 10:00:00 GMT+0800 (中国标准时间)
        output.innerText += dd.toLocaleString() + "\n"; // 2000/1/1 上午10:00:00
 
        var  dd = new Date("2000-01-01T02:00:00");
        output.innerText += dd.toString() + "\n";       // Sat Jan 01 2000 10:00:00 GMT+0800 (中国标准时间)
        output.innerText += dd.toLocaleString() + "\n"; // 2000/1/1 上午10:00:00
 
        var  dd = new Date(Date.UTC(2000, 0, 1, 2, 0, 0));
        output.innerText += dd.toString() + "\n";       // Sat Jan 01 2000 10:00:00 GMT+0800 (中国标准时间)
        output.innerText += dd.toLocaleString() + "\n"; // 2000/1/1 上午10:00:00
 
        var  dd = new Date(2000, 0, 1, 2, 0, 0);
        output.innerText += dd.toString() + "\n";       // Sat Jan 01 2000 02:00:00 GMT+0800 (中国标准时间)
        output.innerText += dd.toLocaleString() + "\n"; // 2000/1/1 上午2:00:00

-----
###字符串操作方法
例子：

    var stringValue = "hello world";
    alert(stringValue.slice(-3));        //"rld"
    alert(stringValue.substring(-3));    //"hello world"
    alert(stringValue.substr(-3));       //"rld"
    alert(stringValue.slice(3, -4));     //"lo w"
    alert(stringValue.substring(3, -4)); //"hel"
    alert(stringValue.substr(3, -4));    //""空字符串

在给slice()和substr()传递一个负值参数时，它们的行为相同。这是因为-3会被转换为8，实际上相等于调用了slice(8)和substr(8)。但substring()方法则返回了全部字符串，因为它将-3转换成了0。

当第二个参数是负数时，这三个方法的行为各不相同。slice()发那个发会把第二个参数转换为7，这就相当于调用了slice(3,7)，因此返回“lo w”。substring()方法会把第二个参数转换为0，使调用变成了substring(3, 0)，而由于这个方法会将较小的数作为开始位置，将较大的数作为结束位置，因此最终相当于调用了substring(0, 3)。substr()也会将第二个参数转换为0，这也就意味着返回包含零个字符的字符串，也就是一个空字符串。

-----
###*`<未解决>`* RegExp类型和正则表达式
模式匹配及捕获组的概念

注：《javascript高级程序设计第三版》 p121 p145

-----
###变量提升(Hoisting)
首先看一个例子：

    var v='Hello World';
    (function(){
        alert(v);              // undefined
        var v='I love you';
    })() 

结果是`undefined`。原因是变量提升会把变量的声明提到作用域的开始位置，但是并不会把赋值也提上来。如下面的例子：

    (function(){
        var a='One';
        var b='Two';
        var c='Three';
    })()

实际它是如下这样的：

    (function(){
        var a,b,c;
        a='One';
        b='Two';
        c='Three';
    })()

所以第一个的示例实际是这样的：

    var v='Hello World';
    (function(){
        var v;
        alert(v);
        v='I love you';
    })()

那么就不难理解结果是`undefined`了。

注：[JavaScript中变量提升 Hoisting](http://www.jb51.net/article/30719.htm) 

-----
###*`<未解决>`* 创建对象、实现继承和实现私有变量的各种方式

注：《javascript高级程序设计第三版》 第六章 第七章

-----
###在闭包中使用this对象
先看下面这个例子：

    var name = "The Window";
    var object = {
        name : "My Object",
        getNameFunc : function(){
            return function(){
                return this.name;
            };
        }
    };
    alert(object.getNameFunc()()); //"The Window"(在非严格模式下)

结果是`The Window`。每个函数在被调用时会自动取得两个特殊变量：this 和 arguments。执行函数object.getNameFunc()时，执行环境是object，所以 this 等于object，函数返回了一个匿名函数(是一个闭包)。该匿名函数立即执行，执行环境是全局而不是object对象，所以它的this等于window。内部函数在搜索这两个变量时，只会搜索到其活动对象为止，永远不可能直接访问外部函数中的这两个变量。因此该闭包使用的this就是window。不过，把外部作用域的this对象保存在一个闭包能够访问到的变量里，就能让闭包访问该对象了，如下示例：

    var name = "The Window";
    var object = {
        name : "My Object",
        getNameFunc : function(){
            var that = this;
            return function(){
                return that.name;
            };
        }
    };
    alert(object.getNameFunc()()); //"My Object"

还有一些情况，this的值可能意外地改变。如下：

    var name = "The Window";
    var object = {
        name : "My Object",
        getName: function(){
            return this.name;
        }
    };

    object.getName(); //"My Object"
    (object.getName)(); //"My Object"
    (object.getName = object.getName)(); //"The Window"在非严格模式下

第三行代码先执行了一条赋值语句，这个赋值表达式的值是函数本身，此时 this 的值发生了改变，结果返回了 `The Window`。

-----
###类、对象、实例的概念
类是对事物的一种定义，对象是实实在在的东西。实例其实就是对象，但是它是有所属的。比如说，我们定义了类 CA，并通过类 CA 创建了对象 objA。我们就可以说 objA 是类 CA 的实例。

参考：
[怎样区分实例，类和对象](http://zhidao.baidu.com/question/10029181.html?qbl=relate_question_1&word=%C0%E0%20%CA%B5%C0%FD%20%B6%D4%CF%F3)

-----
###关于数组的一个注意点
先看下面一个例子：

    var a = [1];
    var f = function(){
        a[a.length] = 2;
        return 3;
    };
    a[a.length] = f();
    alert(a);     // 1,3

正确的结果是`1,3`而不是`1,2,3`。事实上上面的例子是等效于下面的代码的：

    var a = [1];
    var f = function(){
        a[a.length] = 2;
        return 3;
    };
    var tem = a.length;
    a[tem] = f();
    alert(a);

而如果要达到`1,2,3`的效果，应该像下面这样写：

    var a = [1];
    var f = function(){
        a[a.length] = 2;
        return 3;
    };
    var tem = f();
    a[a.length] = tem;
    alert(a);

因此，一个闭包实现的阶乘如下，注意注释部分代码：

    var a = function (){
        var ans = [1];
        return (function f(n){
            if(n<1)
                return -1;

            if(ans.length >= n)
                return ans[n-1];
            // 下面两条语句避免了上述描述的问题
            var tem = f(n-1)*n;
            ans[ans.length] = tem;
            
            return ans[ans.length-1]

        });
    };
    var b = a();

    console.log(b(3)); // 6
    console.log(b(3)); // 6，如果没有避免上述的问题，第二次执行的结果将出错

    b = null;

-----
###立即执行函数

*1. 立即执行函数的定义*

首先使用最容易理解的方式：

    (function(n){console.log(n+1);})(1);     // 方式1
    // function(n){console.log(n+1);}(1);    // 方式2 报错

使用惯性思维理解：方式1首先定义一个匿名函数，并使用第一对圆括号返回该函数，使用第二队圆括号执行函数。而方式2中缺少了第一对圆括号导致报错。

但是这种理解方式无法解释下面这个例子是正确的：

    (function(n){console.log(n+1);}(1));     // 方式3 正确且推荐的方法

按照上文的惯性思维理解，即使最外层加一对圆括号，和方式1应该是等价的，也会报错，但是方式3是不会出错的。事实上，方式1和方式3正确的原因是：

>对于JavaScript. 来说，括弧()里面不能包含语句，所以在这一点上，解析器在解析function关键字的时候，会将相应的代码解析成function表达式，而不是function声明所以，只要将大括号将代码(包括函数部分和在后面加上一对大括号)全部括起来就可以了。

也就是说，无论是方式1还是方式3，其中第一个圆括号起到的作用是让解析器将被其包括的函数解析成函数表达式。而对使函数执行的那对圆括号没有影响，所以它放在里面还是外面是一样的。而且方式3是大部分第三方库的推荐使用的方法。

对于会报错的方式2，我们在函数定义时加上一个函数名，发现解析器将不会报错，如下方式4：

    function fun(n){console.log(n+1);}(1); // 方式4

但是以上的写法等同于以下写法的效果：

    function fun(n){console.log(n+1);};
    (1);

也就是说这两条语句是完全没有关系，函数定义是正确的，但是函数是不会执行的。而且我们想要执行不含参数的函数时会报错，如下代码：

    // function fun(){console.log(1);}();  // 方式5 报错

方式5报错的原因是：

>因为Javascript. 的解析器在解析器解析全局的function或者function内部function关键字的时候， 默认会把大括号解析成function声明，而不是function表达式。也就是说， 会把最后的一对大括号默认解析成一个缺少名字的function，并且抛出一个语法错误信息，因为function声明需要一个名字。

还有另外看上去比较费解的方式：

    ~function(){console.log(1);}();          // 方式6
    void function(){console.log(1);}();      // 方式7

方式6中的~和方式7中的void其实都是是一个运算符，能立即返回后面表达式的值，其他运算符(比如！和+)都可以达到这样的目的。要说区别的话，不同运算符的执行效率是不同的，`void`的效率 > 组运算符`()`的效率 > 位取反`~`运算符。因此，方式7是效率最好的方式，但其实差距也微乎其微。这个结论引用于《[定义并且立即执行JS匿名函数拾遗](http://www.cnblogs.com/walkerwang/archive/2011/06/30/2093923.html)》。

但是为了便于理解，还是建议使用方式3。

*2. 立即执行函数的返回值*

例如如下的使用是正确的：

    var result = function () { return 2; }(); 

但是这种写法容易误导，如果没有最后一对圆括号，result 将指向一个函数，实际上这里result是立即执行函数的返回值。 所以建议还是加上最外层的圆括号：

    var result = (function () { return 2; }()); 

参考：
[js 在定义的时候立即执行的函数表达式(function)写法](http://www.jb51.net/article/33304.htm)
[定义并且立即执行JS匿名函数拾遗](http://www.cnblogs.com/walkerwang/archive/2011/06/30/2093923.html)
[JavaScript学习笔记(十四) 立即执行函数](http://blog.csdn.net/qq838419230/article/details/8030078)

-----

