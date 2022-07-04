# JavaScript

## 1、延迟加载JS有那些方式？

~~~css
延迟加载:async、defer
defer:等html全部解析完成，才会执行js脚本，顺次执行
async:和html解析同步，不按顺次执行js脚本（谁先加载谁先执行）
~~~

## 2、JS的数据类型有哪些？

~~~css
基本类型:string  number  boolean  undefined  null  symbol  bigint
引用类型:object
NaN是一个属性类型，但不是一个具体的数字
~~~

## 3、JS数据类型的考题

~~~javascript
console.log(true+1)//2
console.log('name'+true)//nametrue,字符串和其他类型相加，变连接的形式
console.log(undefined+1)//NaN
console.log(typeof(null))//object
console.log(typeof(NaN))//number
console.log(typeof(undefined))//undefined
~~~

## 4、null和undefined的区别

~~~css
1.作者在设计js的时候先设计的null （最初借鉴了java的语言）
2.null会被隐式转换为0，不容易发现错误
3.现有null后有undefined，出来undefined是为了填补之前的坑

具体区别：JavaScript的最初版本是这样区分的：null是一个表示“无”的对象（空指针对象），转为数值为0；undefined是一个表示“无”的原始值，转为数值时为NaN
~~~

## 5、==和===有什么不同？

~~~css
==:比较的是值
	通过valueOf转换（valueOf()方法通常由JavaScript在后台自动调用）
===：除了比较值，还比较类型
~~~

## 6、JS微任务和宏任务

~~~css
1.js是单线程的语言
2.js代码执行流程：同步执行完-->事件循环
进入事件循环：请求、定时器、事件
	事件循环包含【微任务、宏任务】
微任务：Promise.then
宏任务：setTimeout

要执行宏任务的前提是清空了所有的微任务

流程：同步 ==> 事件循环【微任务、宏任务】 ==> 微任务 ==> 宏任务 ....
~~~

## 7、JS作用域

~~~css
1.除了函数外，js是没有块级作用域的
2.作用域链：内部可以访问外部的变量，但是外部不能访问内部的变量 
	注意：如果内部有，优先查找内部，如果内部没有就查找外部的
3.注意声明变量是用var还是没有写（window.）
4.注意：js有变量提升的机制【变量悬挂声明】
5.优先级：声明变量 > 声明普通函数 > 参数 > 变量提升 
~~~

~~~css
面试的时候怎么看？
1.本层作用域有没有此变量【注意变量提升】
2.注意：js除了函数外没有块级作用域

~~~

## 8、JS对象

~~~css
1.对象是通过new操作符构建出来的，所以对象之间不相等（除了引用外）
2.对象注意引用类型
3.对象的key都是字符串
~~~

## 9、JS判断变量是不是数组，你能写出哪些方法？

~~~css
方式一：isArray
方式二：instanceof 
方式三：原型prototype
	Objext.prototype.toString.call()
方式四：isPrototypeOf()
	Array.prototype.isPrototypeOf()
~~~

## 10、slice是干嘛的？splice是否会改变原数组？

~~~css
slice是用来截取数组，返回一个新数组
	参数可以写(3) (1,3) (-3)
splice用来插入、修改、替换，会改变原数组
~~~

## 11、JS数组去重

~~~javascript
方式一：new set
var arr1 = [1,1,2,2,3,3];
function unique(arr){
    return [ ...new Set(arr)]
}
方式二：indexOf
function unique(arr){
    var brr = [];
    for(var i = 0 ; i < arr.length ;i++ ){
        if(brr.indexOf(arr[i]) == -1){
            brr.push(arr[i])
        }
    }
    return brr;
}
~~~

## 12、找出多维数组的最大值？

~~~javascript
function fnArr(arr){
    var newArr = [];
    arr.forEach((item,index) => {
        newArr.push( Math.max(...item) )
    })
    return newArr;
}
~~~

## 13、给字符串新增方法

~~~javascript
String.protutype.addPrefix = function(str){
    return str + this;
}
console.log('world'.addPrefix('hello'))
~~~

## 14、找出字符串中出现最多次数的字符并统计次数

~~~javascript
var str = 'aassdddddddddgggggg';
var obj = {};
for(var i = 0 ; i < str.length ; i++){
    var char = str.charAt(i)
    if(obj[char]){
        obj[char]++;
    }else{
        obj[char] = 1;
    }
}
var max = 0;
var key = '';
for(var i in obj){
   	if(max < obj[i]){
        key = i;
        max = obj[i];
    }
}
~~~

## 15、new操作符具体做了什么

~~~javascript
1.创建了一个空对象
2.将空对象的原型，指向于构造函数的原型
3.将空对象作为构造函数的上下文
4.对构造函数有返回值的处理判断
~~~

## 16、闭包

~~~javascript
1、闭包是什么？
	闭包就是能够读取其他函数内部变量的函数
2、闭包可以解决什么问题【优点】？
	内部函数可以访问外部函数的局部变量
3、闭包的缺点？
	-变量会驻留在内存中，造成内存损耗问题
		解决：把闭包的函数设置为null
	-内存泄漏[ie]
~~~

## 17、原型链

~~~javascript
1.原型可以解决什么问题？
	对象共享属性和共享方法
2.谁有原型
	函数拥有：prototype
    对象拥有：__poto__
3.对象查找属性或者方法的顺序
	先在对象本身查找 --> 构造函数中查找 --> 对象的原型 --> 构造函数的原型 --> 当前原型的原型中查找
4.原型链
	就是把原型串联起来
    原型链的最顶端是null
~~~

## 18、JS继承有哪些方式？

~~~javascript
方式一：ES6
class Parent{
    constructor(){
        this.age = 18;
    }
}
class Child extends Parent{
    constructor(){
        super();
        this.name="徐海笑"
    }
}
let o1 = new Child();

方式二：原型链继承
function Parent(){
    this.age = 23;
}
function Child(){
    this.name = "徐海笑"；
}
Child.prototype = new Parent();
let o2 = new Child();
方式三：借用构造函数
function Parent(){
    this.age = 23;
}
function Child(){
    this.name = "徐海笑";
    Parent.call(this)
}
let o3 = new Child();
方式四：组合式继承
function Parent(){
    this.age = 23;
}
function Child(){
    this.name = "徐海笑";
    Parent.call(this)
}
Child.prototype = new Parent();
let o4 = new Child();
~~~

## 19、说一下call、apply、bind区别？

~~~javascript
共同点：可以改变this指向
区别：
	1.call、apply可以立即执行，bind不会立即执行，因为bind返回的是一个函数
    2.参数不同，apply第二个参数是数组，call和bind参数是单独罗列 	
~~~





