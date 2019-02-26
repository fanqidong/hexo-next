---
title: 前端知识体系回顾-(JS篇)
categories: 技术
tags: js
copyright: true
reward: true
date: 2018-12-11 13:06:23
---

# JS 篇

# 浩瀚星辰，莫忘心记。——Abner <!-- more -->

## 1、基础语法

Javascript 基础语法包括：变量声明、数据类型、函数、控制语句、内置对象等。

在 ES5 中，变量声明有两种方式，分别是 var 和 function ，var 用于声明普通的变量，接收任意类型，function 用于声明函数。另外，ES6 新增 let、const、import 和 class 等四个命令，分别用以声明 普通变量、静态变量、模块 和 类 。

JS 数据类型共有六种，分别是 String、Number、Boolean、Null、Undefined 和 Object 等， 另外，ES6 新增了Symbol 类型。其中，Object 是引用类型，其他的都是原始类型(Primitive Type)。

原始类型也称为基本类型或简单类型，因为其占据空间固定，是简单的数据段，为了便于提升变量查询速度，将其存储在栈(stack)中(按值访问)。为了便于操作这类数据，ECMAScript
提供了 3 个 基本包装类型 ：Boolean、Number 和 String。基本包装类型是一种特殊的引用类型，每当读取一个基本类型值的时候，JS 内部就会创建一个对应的包装对象，从而可以调用一些方法来操作这些数据。

引用类型由于其值的大小会改变，所以不能将其存放在栈中，否则会降低变量查询速度，因此其存储在堆(heap)中，存储在变量处的值是一个指针，指向存储对象的内存处(按址访问)，对于引用类型的值，可以为其添加属性和方法，也可以改变和删除其属性和方法；但基本类型不可以添加属性和方法。

Javascript 可以通过 typeof 来判断原始数据类型，但不能判断引用类型，要知道引用类型的具体类型，需要通过 Object 原型上的toString 方法来判断。

JS 中的函数存在着三种角色：普通函数、构造函数、对象方法。同一个函数，调用方式不同，函数的作用不一样，所扮演的角色也不一样。直接调用时就是普通函数，通过 new 创建对象时就是构造函数，通过对象调用时就是方法。

JS 常用的内置对象有 window、Date、Array、JSON、RegExp等，window 是浏览器在执行脚本时创建的一个全局对象，主要描述浏览器窗口相关的属性和状态，这个后面会讲到，Date 和 Array使用场景最多，JSON 主要用于对象的序列化和反序列化，还有一个作用就是实现对象的深拷贝。RegExp 即正则表达式，是处理字符串的利器。

##  2、函数原型链

JS 是一种基于对象的语言，但在 ES6 之前是不支持继承的，为了具备继承的能力，Javascript 在 函数对象
上建立了原型对象 prototype，并以函数对象为主线，从上至下，在 JS 内部构建了一条 原型链 。原型链把一个个独立的对象联系在一起，Object
则是所有对象的祖宗， 任何对象所建立的原型链最终都指向了 Object，并以 Object 终结。

简单来说就是建立了变量查找机制，当访问一个对象的属性时，先查找对象本身是否存在，如果不存在就去该对象所在的原型连上去找，直到 Object 对象为止，如果都没有找到该属性才会返回 undefined。因此，我们可以通过原型链来实现 JS 继承。

## 3、函数作用域

函数作用域就是变量在声明它们的函数体以及这个函数体嵌套的任意函数体内都是有定义的。因此， JS 中没有块级作用域，只有函数作用域，这种设计导致 JS 中出现了 变量提升 的问题。简单来说就是，将变量声明提升到它所在作用域的最开始的部分，为了解决变量提升带来的副作用，ES6 新增了let 命令来声明变量，let 所声明的变量只在 let 命令所在的代码块内有效，所以不存在变量提升问题。

## 4、this 指针

this 指针存在于函数中，用以标识函数运行时所处的上下文。函数的类型不同，this 指向规则也不一样：对于普通函数，this始终指向全局对象 window；对于构造函数，this 则指向新创建的对象；对于方法，this 指向调用该方法的对象。另外，Function 对象也提供了 call、apply和 bind 等方法来改变函数的 this 指向，其中，call 和 apply 主动执行函数，bind 一般在事件回调中使用，而 call 和 apply的区别只是参数的传递方式不同。

如果往深的去理解，无论什么函数，this 是否被改变， 本质上，this 均指向触发函数运行时的那个对象。而在函数运行时，this 的值是不能被改变的。

## 5、new 操作符

  函数的创建有三种方式，即 显式声明、匿名定义 和 new Function()。前面提到，JS 中的函数即可以是函数，也可以是方法，还可以是构造函数。当使用 new 来创建对象时，该函数就是构造函数，JS 将新对象的原型链指向了构造函数的原型对象，于是就在新对象和函数对象之间建立了一条原型链，通过新对象可以访问到函数对象原型 prototype 中的方法和属性。

## 6、闭包

通俗来讲，闭包是一个具有独立作用域的静态执行环境。和函数作用域不同的是，闭包的作用域是静态的，可以永久保存局部资源，而函数作用域只存在于运行时，函数执行结束后立即销毁。因此，闭包可以形成一个独立的执行过程，关于闭包知识请参考阮一峰老师的详细讲解 [阮一峰闭包详解](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)

## 7、单线程和异步队列

Javascript是单线程语言，在浏览器中，当 JS 代码被加载时，浏览器会为其分配一个主线程来执行任务(函数)，主线程会形成一个全局执行环境，执行环境在栈中采用后进先出(LIFO)的顺序来执行代码块，以保证所有的函数能按照正确的顺序被执行。但在浏览器中，有一些任务是非常耗时的，比如 ajax 请求、定时器、事件等，为了保证非耗时任务不受影响，Javascript在执行环境中维护了一个异步队列(也叫工作线程)，并将这些耗时任务放入队列中进行等待，这些任务的执行时机并不确定，只有当主线程的任务执行完成以后，主线程才会去检查异步队列中的任务是否需要开始执行。JS 中的 setTimeout 和 setInterval 就是典型的异步操作，它们会被放入异步队列中等待，即使 setTimeout(0)
也不会被立即执行，需要等到当前同步任务结束后才会被执行。

## 8、异步通信 Ajax 技术

Ajax 是浏览器专门用来和服务器进行交互的异步通讯技术，其核心对象是 XMLHttpRequest，通过该对象可以创建一个 Ajax 请求。Ajax 请求是一个耗时的异步操作，当请求发出以后，Ajax提供了两个状态位来描述请求在不同阶段的状态，这两个状态位分别是 readyState 和 status ，readyState 通过5个状态码来描述一个请求的 5 个阶段：

0 - 请求未发送，初始化阶段

1 - 请求发送中，服务器还未收到请求

2 - 请求发送成功，服务器已收到请求

3 - 服务器处理完成，开始响应请求，传输数据

4 - 客户端收到请求，并完成了数据下载，生成了响应对象

status 用于描述服务端对请求处理的情况，200 表示正确响应了请求，404 表示服务器找不到资源，500 代表服务器内部异常等等。

Ajax 对象还可以设置一个 timeout 值，代表超时时间，切记：timeout 只会影响readyState，而不会影响 status，因为超时只会中断数据传输，但不会影响服务器的处理结果。 如果 timeout 设置的不合理，就会导致响应码status 是 200，但 response 里却没有数据，这种情况就是服务器正确响应了请求，但数据的下载被超时中断了。

为了防止 XSS 攻击，浏览器对 Ajax 请求做了限制，不允许 Ajax 跨域请求服务器，只允许请求和当前地址同域的服务器资源。但不限制脚本和标签发送跨域请求，比如
script 和 img 标签，因此可以利用脚本跨域能力来实现跨域请求，即 JSONP 的原理。

JSONP 虽然可以解决跨域问题，但只能是 get 请求，并且没有有效的错误捕获机制，为了解决这个问题，XMLHttpRequest Level2 提出了CORS 模型，即 跨域资源共享， 它不是一个新的 API，而是一个标准规范，当浏览器发现该请求需要跨域时，就会自动在头信息中添加一个 Origin字段，用以说明本次请求来自哪个源。服务器根据这个值，决定是否同意这次请求。

随着移动端的快速发展，Web 技术的应用场景正在变得越来越复杂， 关注点分离 原则在系统设计层面就显得越来越重要，而 XMLHttpRequest 是Ajax 最古老的一个接口，因而不太符合现代化的系统设计理念。因此，浏览器提供了一个新的 Ajax 接口，即 Fetch API ，Fetch API 是基于 Promise 思想设计的，更符合关注点分离原则。

## 9、模块化

历史上，Javascript 规范一直没有模块(module)体系，即无法将一个大程序拆分成互相依赖的小文件，再用简单的方法拼装起来。在 ES6之前，为了实现 JS 模块化编程，社区制定了一些模块加载方案，最主要有 CMD 和 AMD 两种，分别以 commonjs 和 requirejs 为代表。ES6在语言标准的层面上，实现了模块化编程，其设计思想是，尽量静态化，使得编译时就能确定模块的依赖关系，即编译时加载，而 CMD 和 AMD 是在运行时确定依赖关系，即运行时加载。

## 10、Node.js

Node.js 是一个基于 Chrome V8 引擎的 JavaScript运行环境，它的运行不依赖于浏览器作为宿主环境，而是和服务端程序一样可以独立的运行，这使得 JS 编程第一次从客户端被带到了服务端，Node.js 在服务端的优势是，它采用单线程和异步 I/O 模型，实现了一个高并发、高性能的运行时环境。相比传统的多线程模型，Node.js 实现简单，并且可以减少资源开销。

## 11、ES6

ES6 是 ECMAScript 6.0
的简写，即 Javascript 语言的下一代标准，已经在 2015 年 6 月正式发布了，它的目标是让 JS 能够方便的开发企业级大型应用程序，因此，ES6 的一些规范正在逐渐向 Java、C#等后端语言标准靠近。ES6规范中，比较重大的变化有以下几个方面：

新增 let、const 命令 来声明变量，和 var 相比，let声明的变量不存在变量提升问题，但没有改变 JS 弱类型的特点，依然可以接受任意类型变量的声明；
const声明的变量不允许在后续逻辑中改变，提高了 JS 语法的严谨性。

新增解构赋值、rest 语法、箭头函数，这些都是为了让代码看起来更简洁，而包装的语法糖。

新增模块化，这是 JS 走向规范比较重要的一步，让前端更方便的实现工程化。

新增类和继承的概念，配合模块化，JS 也可以实现高复用、高扩展的系统架构。

新增模板字符串功能，高效简洁，结束拼接字符串的时代。

新增 Promise 对象，解决异步回调多层嵌套的问题。