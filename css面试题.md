# css

## 1、介绍以下css盒子模型

~~~css
css的盒子模型有哪些：标准盒子模型、IE盒子模型
css的盒子模型区别：
	标准盒子模型：margin+border+padding+content
	IE盒子模型：margin+content
通过css如何转换盒子模型：
	box-sizing:content-box;/*标准盒子模型*/
	box-sizing:border-box;/*IE盒子模型*/
~~~

## 2、line-height和height的区别

~~~css
line-height:是每一行文字的高，如果文字换行则整个盒子高度会增大
height:是一个固定的值，就是盒子的高度
~~~

## 3、css选择符有哪些？哪些属性可以继承？

~~~css
css选择符：
通配符（*）
id选择器（#）
类选择器（.）
标签选择器（div、p、h1）
相邻选择器（+）
后代选择器（ul li）
子元素选择器（>）
属性选择器（a[href]）
~~~

~~~css
css属性那些可以继承：
文字系列：font-size、color、line-height、text-algin...
***不可继承属性：border、padding、margin

~~~

## 4、css优先级算法如何计算？

~~~css
优先级比较：!inportant > 内联样式 > id > class > 标签 > 通配
css权重计算：
第一：内联样式		        权重值：1000
第二：id选择器 			权重值：100
第三：类选择器  		    权重值：10
第四：标签&为元素选择器      权重值：1
第五：通配、>、+			权重值：0
~~~

## 5、用css画一个三角形

~~~css
用边框画（border）
    div{
        width: 0;
        height: 0;
        border:100px solid transparent;
        border-top-color: red;
    }
~~~

## 6、一个盒子不给宽高如何实现垂直水平居中

### 方式一：弹性盒

~~~css
<style>
    .container{
        width: 200px;
        height: 200px;
        border:1px solid goldenrod;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .main{
        background-color: yellow;
    }
</style>
<body>
    <div class="container">
        <div class="main">123</div>
    </div>
</body>
~~~

### 方式二：同通过定位，然后加 tranfrom：translate（-50%，-50%）

~~~css
<style>
    .container{
        width: 200px;
        height: 200px;
        border:1px solid goldenrod;
        position: relative;
    }
    .main{
        background-color: yellow;
        position: absolute;
        top: 50%;
        left: 50%;
        transform:translate(-50%,-50%);
    }
</style>
<body>
    <div class="container">
        <div class="main">123</div>
    </div>
</body>
~~~

## 7、display有哪些值？

~~~css
none		隐藏元素
block		把元素转换成块元素
inline		把元素转换成内联元素
inline-block 把元素转换成行内块元素
~~~

## 8、对BFC规范（格式化上下文）的理解？

~~~css
BFC就是页面上一个隔离的独立容器，容器里面的子元素不会影响到外面的元素
1.BFC：块级格式化上下文
2.BFC的原则：如果一个元素具有BFC，那么这个元素再怎么弄，都不会影响到外面的元素
3.如何触发BFC：
	浮动的值非none
	overflow的值非visible
	display的值为：inline-block、table-cell...
	position的值为absolute、fixed
~~~

## 9、清除浮动有哪些方式？

~~~css
1.触发BFC
2.多创建一个盒子，添加样式:clear:both;
3.after方式
    ul:after{
        content:'',
        display:block;
        clear:both;
    }
~~~

## 10、在网页中应该使用奇数还是偶数字体？为什么？

~~~css
偶数：让文字在浏览器上表现得更好看
另外说明：ui给前端设计图一般都是偶数，这样不管是布局也好，转换成px也好，方便一点
~~~

## 11、position有那些值？分别根据什么定位的？

~~~css
static[默认]:没有定位
fixed:固定定位，相对于浏览器的窗口定位
relative:相对于自身定位，不脱离文档流
absolute:相对于第一个有relative的父元素，脱离文档流
~~~

## 12、双飞翼布局

~~~html
<style>
body{
    width: 100vw;
    height: 100vh;
}
body > div{
    float: left;
}
.l{
    width: 200px;
    background-color: greenyellow;
    margin-left: -100%;
}
.c{
    width: 100%;
    background-color: red;
}
.c .main{
    padding: 0 200px;
}
.r{
    width: 200px;
    background-color: darkcyan;
    margin-left: -200px;
}
</style>
<body>
    <div class="c">
        <div class="main">中</div>
    </div>
    <div class="l">左</div>
    <div class="r">右</div>
</body>
~~~

## 13、什么是CSS reset？

~~~css
是一个css文件，用来重置css样式
Normalize.css 为了增强跨浏览器渲染的一致性，一个css重置样式库
~~~

## 14、什么是CSS Sprite

~~~css
1.是什么？
	把多个小图标合并成一张大图片
2.优缺点
	优点：减少了http请求的次数，提升性能
	缺点：维护比较差（图pain位置进行修改，尺寸进行修改）
~~~

## 15、display:none和visibility:hidden的区别

~~~css
display:none;让元素直接消失，会影响布局问题；
visibility:hidden;让元素消失，但仍然占用空间，而且visibility具有继承性
~~~

## 16、opacity和rgba的区别

~~~css
opacity属性的值可以被子元素继承（0完全透明）
rgba属性值不会被继承
~~~

