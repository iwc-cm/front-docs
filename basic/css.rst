##################################################
 CSS 基础
##################################################

如果你急于求成，建议你直接看 react 部分，这部分可以以后再看。

前提
========================

#. css 颜色

    颜色有

    * 命名表示法: red, 通过颜色名称表示颜色，这种方法表示的颜色数量有限。
    * 16进制表示: #ff0000, 每两位表示一个颜色的值，分别是 rbg三种颜色的比例。
    * rgb格式: rgb(255, 0, 0), 三位分别表示 rgb 的颜色比例，范围 0-255.
    * hls格式: 不常用，不做介绍。

    以上三种颜色都是 三个变量，但是都可以选择性地加上第四个变量，表示透明度，也不做介绍。

#. 大小单位

    大小通常使用像素为单位: px. 如宽、高、字体。也可以使用百分比: 50%, 或者以字符数为单位: em 。

#. 使用css

    css最简单的使用方法就是通过 style 内联

    ::

        <div style="color: red">这段文字是红色</div>


常用css
=======================

要看所有css，到 http://www.w3school.com.cn/cssref/index.asp 快速预览， 或者点击去查看。

或者到 http://www.w3school.com.cn/css/index.asp 系统地学习。

比较常用的css：

    * margin: 外边距
    * padding: 内边距
    * color: 颜色
    * border: 边框
    * width/height: 宽高
    * font: 字体
    * background: 背景

案例::

    <div style="width: 150px;height: 50px; background: red">这是一个框</div>

渲染如下

.. raw:: html

    <div style="width: 150px;height: 50px; background: red">这是一个框</div>

与 HTML 结合
========================

一般来说，直接将css样式通过 style 属性内联到html中，作用有限。
因为需要针对每一个元素单独写一个样式。 所以就有必要用到CSS选择器。
对元素批量设置样式。

要对元素批量设置样式，需要将CSS放到 ``<style></style>`` 标签中。

css选择器
-----------------------

选择器常用的有三种

#. 通过 id 选择

    这种方式使用 ``#`` 开头。

    ::

        <style>
            #mydiv {
                width: 150px;
                height: 50px; 
                background: red;
            }
        </style>

        <div id="mydiv">这是一个框</div>

    上面 style 标签也是包含在html中的， 其中 css 样式
    首先选定需要修饰的元素，然后在大括号中说明加什么特效。

    结果如下

    .. raw:: html

        <style>
            #mydiv {
                width: 150px;
                height: 50px; 
                background: red;
            }
        </style>

        <div id="mydiv">这是一个框</div>

#. 通过标签选择，如 p/h1/h2/table 等

    这种方式无需使用任何开头字符

    ::

        <style>
            div {
                background: red;
            }
            p {
                background: green;
            }
        </style>

        <div>我是div</div>
        <p>我是段落</p>

    效果如下

    .. raw:: html

        <style>
            #mydiv1 div {
                background: red;
            }
            #mydiv1 p {
                background: green;
            }
        </style>

        <div id="mydiv1">
            <div>我是div</div>
            <p>我是段落</p>
        </div>

#. 通过class选择

    通过class的选择方式使用 ``.`` 开头

    这是最广泛的选择方式，因为class可以标示一类控件。

    ::

        <style>
            .red-div {
                background: red;
            }
            .big-div {
                font: 25px bolder;
            }
        </style>

        <div class="red-div">我是红色</div>
        <div class="red-div">我也是红色</div>
        <div class="big-div">我字很大</div>
        <div class="red-div big-div">我红色而且字很大</div>

    效果如下

    .. raw:: html

        <style>
            .red-div {
                background: red;
            }
            .big-div {
                font: 25px bolder;
            }
        </style>

        <div class="red-div">我是红色</div>
        <div class="red-div">我也是红色</div>
        <div class="big-div">我字很大</div>
        <div class="red-div big-div">我红色而且字很大</div>

#. 选择器的层叠和组合


    上面说了三种选择器

        * id 选择器
        * class 选择器
        * tab 选择器

    另外html文档是 xml 文档，其中的元素是一层一层嵌套的。所以存在选择器的嵌套。

        * #mydiv .red-div ：选择id为mydiv元素下面的所有 class=red-div 的下层元素，不必是直接子元素。
        * #mydiv>.red-div ：和上面差不多，但是必须是直接子元素。
        * .red-div, .big-div: 同时选中 class=red-div 和 class=big-div的元素，或的关系。
        * .red-div.big-div: 选中 class=red-div 且 class=big-div的元素，且的关系。
        * #mydiv .red-div ：选择id为mydiv元素并且class=red-div 的元素。

#. 其他选择器

    css 选择器有很多种形式，比如状态选择（hover）、孩子选择（nth-child）等。不介绍。

引用css
------------------

上面介绍了 style 内联和html的 style 标签使用css样式。

更加通用的做法是将css定义在一个 css文件中，html 通过超链接引入.

::

    <link rel="stylesheet" href="/static/mystyle.css" type="text/css">

另外需要知道 css 有很多变种，如 scss，这里也不做介绍。
