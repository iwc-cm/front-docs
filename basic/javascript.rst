####################################
JavaScript 介绍
####################################


JavaScript 作用
===========================

html用来定义文档，css用来添加效果。但是这两个东西终究是静态的，一旦创建就无法修改。为了得到动态页面，有两种方法。

#. 后端渲染

    HTML 本质上是给xml格式的字符串，后端先构造出为想要的html字符串，发送给前端。

    这种方法在某些情况下代价很高，因为无论html改动多小，都需要后端将 html 完全构造一遍，传回浏览器。

#. 前端渲染

    通过在浏览器中嵌入 JavaScript。

    JavaScript 是前端编程语言，可以动态生成、修改、删除 xml 元素，也能增加事件、修改元素属性、
    修改元素id/class/css。几乎可以完全操控当前的html。

    前端编程也就是使用 JavaScript 编程。

下面是一个例子

.. code-block:: html

    <html>
        <head>
            <meta charset="utf-8" />
            <title>测试网页</title>
        </head>
        <body>
            <script>
                function addOne(){
                    var newLi =  document.createElement('li');
                    newLi.innerText="一个元素";

                    var dom = document.getElementById("my-list");
                    dom.appendChild(newLi)
                }
            </script>
            
            <div>点击下面的按钮，可以增加列表</div>
            <button onClick="addOne()">增加一个</button>
            <ol id="my-list"></ol>
        </body>
    </html>

.. raw:: html

    <a target="_blank" href="../_static/javascript.html">查看效果</a>


JavaScript 一些注意点
===========================

lambda表达式
------------------------

JavaScript 引入和函数式编程的概念，所以介绍一下箭头函数。

.. code-block:: javascript

    function add(a, b) {
        return a + b;
    }

    // 使用箭头定义这个函数。这种方式是等价的。
    (a, b) => {
        return a + b;
    }

    // 对于这种只有一个return语句的简单的函数，可以去掉大括号，简化return语句。
    (a, b) => a + b

    // 简化形式的函数体加上括号可读性更好一点。也能避免一些错误。
    (a, b) => (a + b)

    // 将这个箭头函数赋值给一个变量
    let add = (a, b) => (a + b)
    add(1, 2) // 返回 3

this
---------------

JavaScript 中的this是个很具有迷惑性的东西。

::

    class OtherClass {
        do_call(func) {
            func()
        }
    }

    class TestClass{
        a = 9
        myfunc() {
            console.log(this.a)
        }

        wrongCall() {
            new OtherClass().do_call(this.myfunc)
        }
    }

正常情况下调用 ``TestClass.myfunc`` 是没有问题的。

一旦将myfunc传递给其他对象调用, 比如调用 ``TestClass.wrongCall`` ，就会出现问题， ``this.a`` 不存在。
因为函数中 this 所指向的上下文是运行时动态获取的, 当myfunc传递到 OtherClass 后，this指向的就是 OtherClass 了, 不存在 ``this.a`` 。

正确的做法是使用 箭头函数，因为箭头函数会保存函数定义时的上下文。

::

    class OtherClass {
        do_call(func) {
            func()
        }
    }

    class TestClass{
        a = 9
        myfunc = () => {
            console.log(this.a)
        }

        wrongCall() {
            new OtherClass().do_call(this.myfunc)
        }
    }

Array操作
----------------------

.. code-block:: javascript

    let datas = ["a", "b", "c"]
    // 添加元素
    datas.push('d')
    // 挨个处理
    datas.map(item => (item+item)) // 输出： ["aa", "bb", "cc", "dd"]


window/document
----------------------------

javascript 中有两个全局对象 - window/document

document

    保存当前html的所有元素。可以用于增删改查元素。

window

    保存当前浏览器窗口的信息。比如 当前url、浏览器窗口的宽高。

