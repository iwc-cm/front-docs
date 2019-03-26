#################################
Html 基础
#################################

Html介绍
===========================

html 本质是一个 XML 文档。

最简单的 html 可以是一个 text 文档，这时，所有文字都是在一行的，当需要对某些文字加上特效时，
可以使用 XML 标签包围那段文字。标准一点的 html ，
每段文字都需要包含在 XML 标签中。

如果希望尝试下面的例子，可以新建一个 txt 文件，修改后缀名为 ``.html`` .
写入下面的html内容， 右键使用 chrome、firefox 等浏览器打开。就能预览效果。

最简单的HTML

    ::

        这是一行，
        这也在同一行
    
    渲染为html如下

    .. raw:: html

        这是一行，
        这也在同一行

html基础元素
=======================

段落 paragraph

    ::

        <p>这是一个段落</p>
        <p>这是另一个段落</p>

    .. raw:: html

        <p>这是一个段落</p>
        <p>这是另一个段落</p>

标题 header

    标题分为很多种，有一级标题、二级标题……六级标题, 
    对应的分别是 h1/h2/h3...h6 标签, 一级标题最大，后面的一次减小。

    ::

        <h1>一级标题</h1>
        <h2>二级标题</h2>
        <h3>三级标题</h3>
        <h4>四级标题</h4>
        <h5>五级标题</h5>
        <h6>六级标题</h6>

    渲染为html如下

    .. raw:: html

        <h1>一级标题</h1>
        <h2>二级标题</h2>
        <h3>三级标题</h3>
        <h4>四级标题</h4>
        <h5>五级标题</h5>
        <h6>六级标题</h6>

有序列表 ordered list

    列表稍微复杂一些，需要使用两个标签。
    渲染出来后是一个带有序号的列表。

    #. ol 表示有序列表
    #. li 表示每一项。 （list）

    ::

        <ol>
            <li>这是第一项</li>
            <li>这是第二项</li>
            <li>这是第三项</li>
        </ol>
    
    渲染为html如下

    .. raw:: html

        <ol>
            <li>这是第一项</li>
            <li>这是第二项</li>
            <li>这是第三项</li>
        </ol>


无序列表 unordered list

    和有序列表类似，但是使用 ul 标签。
    渲染出来后是一个不带序号的列表。

    ::

        <ul>
            <li>这是第一项</li>
            <li>这是第二项</li>
            <li>这是第三项</li>
        </ul>
    
    渲染为html如下

    .. raw:: html

        <ul>
            <li>这是第一项</li>
            <li>这是第二项</li>
            <li>这是第三项</li>
        </ul>

表格

    表格更复杂一些，使用了四种标签。

    * table: 表示一个表格
    * tr: 表示表格的一行
    * td: 表示一个单元格
    * th: 和td类似，表示一个表头单元格

    ::

        <table>
            <tr>
                <th>姓名</th>
                <th>年龄</th>
            </tr>
            <tr>
                <td>张三</td>
                <td>21</td>
            </tr>
            <tr>
                <td>李四</td>
                <td>22</td>
            </tr>
        </table>
    
    渲染为html如下

    .. raw:: html

        <table  width="300" border="1" cellpadding="0" cellspacing="0" bordercolor="black" style="border-collapse:collapse;">
            <tr>
                <th>姓名</th>
                <th>年龄</th>
            </tr>
            <tr>
                <td>张三</td>
                <td>21</td>
            </tr>
            <tr>
                <td>李四</td>
                <td>22</td>
            </tr>
        </table>

图片 - image

    将图片链接贴到网页。

    ::

        <img src="//www.baidu.com/img/bd_logo1.png" />
    
    渲染为html如下

    .. raw:: html

        <img src="//www.baidu.com/img/bd_logo1.png" />

交互控件 - input

    交互控件都是 input, 通过type字段指定其类型。

    其实还有check， 就不介绍了。

    ::

        <input type="password" placeholder="密码输入框"/>
        <input placeholder="普通输入框"/> <br />
        <input type="button">这是一个按钮</input>
    
    渲染为html如下

    .. raw:: html

        <input type="password" placeholder="密码输入框"/>
        <input placeholder="普通输入框"/> <br />
        <input type="button">这是一个按钮</input>

div

    div 可谓是前端开发中最广泛使用的标签。

    div 本身的表现形式是换行， 和 p 差不多。但是可以通过各种css添加样式表现出各种形态。
    如果需要调整某一块的样式，一般都先通过 div 包一层，然后在上面加 样式。

    ::

        <div>这是一个div</div>
        <div>这是第二个div</div>
    
    渲染为html如下

    .. raw:: html

        <div>这是一个div</div>
        <div>这是第二个div</div>

span

    span 也比较常用，和 div 差不多。和 div 的区别在于，其默认情况下不会换行。

    ::

        <span>这是一个span</span>
        <span>这是第二个span</span>
    
    渲染为html如下

    .. raw:: html

        <span>这是一个span</span>
        <span>这是第二个span</span>

Html控件属性
=============================

在上面的例子中，img 元素就拥有 src 属性， input元素也拥有 type 属性.

.. code-block:: html

    <img src="//www.baidu.com/img/bd_logo1.png" />
    <input type="button">这是一个按钮</input>

html 控件属性直接写在标签里面。

有一些比较常用的属性。

#. id

    id 用来唯一标示一个元素, 即命名，一个页面不允许两个元素id相同
    （其实也不是强制的，如果一样的话，会出现一些问题。）。

    任何元素都可以有id。

    .. code-block:: html
    
        <img id="my-image" src="//www.baidu.com/img/bd_logo1.png" />

#. class

    class 和 id 类似，也是一个名字，但是可以重复，而且鼓励重复，
    用来标示同一类的一组控件。比如居右的一组控件可能有一组相同的class。
    对于样式复用很有帮助。

    一个控件可以有多个 class，通过空格隔开。

    .. code-block:: html
    
        <input class="myinput hisinput" type="button">这是一个按钮</input>
        <input class="myinput" type="button">这是另一个按钮</input>

#. rowspan/colspan

    table 专用，用来制作跨行跨列的表格。不多介绍。

#. style

    用来定义内联css样式，后面会说。不做介绍。

html/head/body
================================

一般不会直接在一个文件中写 html 元素，而是有一个骨架，主要分为 head/body.

html骨架如下

.. code-block:: html

    <html>
        <head>
            <title>这是一个测试页面</title>
        </head>
        <body>
            <div>这是页面正文内容</div>
        </body>
    </html>

title 中的内容会显示在浏览器中的标签tab上。

body 中写 html 内容。



