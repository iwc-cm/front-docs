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

    ::

        <table></table>
    
    渲染为html如下

    .. raw:: html

        <table></table>

图片

    ::

        <table></table>
    
    渲染为html如下

    .. raw:: html

        <table></table>

交互控件

    ::

        <table></table>
    
    渲染为html如下

    .. raw:: html

        <table></table>

span

    ::

        <table></table>
    
    渲染为html如下

    .. raw:: html

        <table></table>

div

    ::

        <table></table>
    
    渲染为html如下

    .. raw:: html

        <table></table>

Html控件属性
=============================

html/head/body
================================

    ::

        <table></table>
    
    渲染为html如下



