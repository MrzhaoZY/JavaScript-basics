> # 	Web APIs阶段
>
> - Web APIs 是 W3C 组织的标准
>
> - BOM 和 DOM
>
> - Web APIs是JS做独有的部分
>
> - 主要学习页面交互功能
>
> - Web APis 和 JS 基础关联性
>
>   
>
>   JS基础学习ECMAScript 基础语法为后面作铺垫， Web APIs 是JS 的应用， 大量使用JS基础语法做交互效果



> ​	API
>
> - (Application Programming Interface, 应用程序编程接口)  是一些预先定义的函数， 目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节
>
>   - 简单理解： API 是给程序员提供的一种工具， 以便能更轻松的实现想要完成的功能
>
>   Web  API
>
> - Web API 是浏览器提供的一套操作浏览器功能和页面元素的API（BOM 和 DOM）
>
>   现阶段我们主要针对于浏览器讲解常用的API， 主要针对浏览器做交互效果。
>
>   因为Web API很多， 所以这个阶段称为  Web APIs



- - - API 和 Web API 总结

    1. API 是为我们程序员提供的一个接口， 帮助我们实现某种功能， 我们会使用就可以了， 不必纠结内部如何实现
    2. Web API 主要是针对于浏览器提供的接口， 主要用于浏览器做交互效果。
    3. Web API 一般都有输入和输出（函数的传参和返回值）， Web API 跟多都是方法（函数）
    4. 结合 内置对象 的学习思路

# 1-DOM

### 1.1 DOM

> ​		文档对象模型（Document Object Model 简称DOM）， 是W3C 组织推荐的处理可扩展标记语言（HTML 或者 XML）的标准编程接口
>
> W3C 已经定义了一系列DOM 接口， 通过这些DOM接口可以改变网页的内容、结构和样式

 **DOM树**

- 文档： 一个页面就是一个文档，DOM 中使用 document表示
- 元素： 页面中的所有标签都是元素， DOM中使用element表示
- 节点： 网页中所有的内容都是节点（标签，属性，文本，注释等）, DOM中使用node 表示

<!-- DOM 把以上所有内容都看做是对象-->

### 1.2 获取元素

> ​		获取页面元素的方式：
>
> - 根据ID 获取
> - 根据标签名获取
> - 通过HTML5 新增的方法获取
> - 特殊元素获取

##### 1.2.1 根据ID 获取

​		getElementById()

<script>
    // 1.因为我们文档页面从上往下加载， 所以先得有标签， 所以我们script 写到标签的下面
        // 2.get 获得 elemen 元素 by 通过 驼峰命名法
        // 3.参数 id 是大小写敏感的字符串
        // 4. 返回的是一个元素对象
        var timer = document.getElementById('time');
        console.log(timer);
        console.log(typeof timer);
        // 5. console.dir 打印我们返回的元素对象 更好的查看里面的属性和方法
        console.dir(timer);
</script>

##### 1.2.2 根据标签名获取

​		getElementByTagName();  返回带有指定标签名的对象的集合

​		element.getElementByTagName();  可以得到这个元素里面的某些标签

<script>
        //1. 返回的是  获取过来的元素对象的集合  以伪数组的形式存储的
        var lis = document.getElementsByTagName('li');
        console.log(lis);
        console.log(lis[0]);
        //2. 我们想要一次打印里面的元素对象 采用遍历的方式
        for ( var i = 0; i <lis.length; i++) {
            console.log(lis[i]);
        }
        // 得到的元素是动态的
    //3. element.getElementByTagName();  可以得到这个元素里面的某些标签
    var nav = document.getElementById('nav');
    var lis1 = nav.getElementsByTagName('li');
    console.log(lis1);


​    

##### 1.2.3 通过H5新增的方法获取

​		document.getElementsByClassName('类名'); 

​		根据类名返回元素对象集合

​		querySelector('选择器'); 返回指定选择器的第一个元素对象  切记里面的选择器要加符号  .box #nav 

​		 querySelectorAll('选择器'); // 根据指定选择器返回所有元素的集合

##### 1.2.4 获取特殊元素

<script>
    var bodyEle = document.body;
        console.log(bodyEle);
        console.dir(bodyEle);

        //2. 获取Html 元素
        // var htmlEle = document.html;    ×
        var htmlEle = document.documentElement;
        console.log(htmlEle);
</script>

### 1.3 事件基础

##### 1.3.1 事件概述

> ​	javascript 使我们有能力创建动态页面， 而事件是可以被JavaScript 侦测到的行为。
>
> 简单理解： 触发... 响应机制

##### 1.3.2 事件三要素

<script>
    // 1. 事件是由三部分组成： 事件源 事件类型 事件处理程序  ==> 事件三要素 
        //(1) 事件源 事件被触发的对象  谁  按钮
        var btn = document.getElementById('btn');

        //(2) 时间类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过  还是键盘按下
        //(3) 事件处理程序  通过一个函数赋值的方式 完成
        btn.onclick = function() {
            alert('hello');
        }
</script>

##### 1.3.3 执行事件的步骤

> 1. 获取事件源
> 2. 注册事件(绑定事件)
> 3. 添加事件处理程序(采取函数赋值的形式)

##### 1.3.4 常见的鼠标事件

1. onclick			鼠标点击左键触发
2. onmouseover   鼠标经过触发
3. onmouseout     鼠标离开触发
4. onfocus              获得鼠标焦点触发
5. onblur                失去鼠标焦点触发
6. onmousemove 鼠标移动触发
7. onmouseup      鼠标弹起触发
8. onmousedown 鼠标按下触发

### 1.4 操作元素

> js 的DOM操作可以改变网页内容、结构和样式， 我们可以用 DOM 操作元素来改变元素里面的内容，属性等。