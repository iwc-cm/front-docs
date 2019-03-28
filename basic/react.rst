#################################
react 基础
#################################


怎么启动一个React项目
=================================

外网使用 create-react-app.

内网下载 antd_template. 直接修改 ``src/pages/Home/index.tsx``

一些概念
=====================

控件的组合--组件
---------------------------

react有一个组件的概念。可以将一大堆 html标签 封装为一个组件，从而做到复用。

组件有两种。

第一种比较简单，直接是一个函数:

    .. code-block:: javascript
    
        function MyComponent() {
            return <div>
                <input />
                <input type="button"/>
            </div>
        }

第二种是一个类，需要实现render方法, 继承 ``React.Component`` 。

    .. code-block:: javascript
    
        class MyComponent extends React.Component {
            function render() {
                return <div>
                    <input />
                    <input type="button"/>
                </div>
            }
        }

入口
---------------------------

一般来说，一个React页面的初始状态是一个空页面。首先将一个顶层组件塞到html中，
这个顶层组件又调用了很多其他子组件。合在一起看就是嵌套的 xml 。

事件
---------------------------

每一个html元素都可以监听事件，比如鼠标点击事件、键盘事件等。比较常用的就是 onClick。
可以注册一个函数到事件上，事件一旦触发，就会执行那个函数

    .. code-block:: javascript
    
        function say_click(){
            console.log("do click")
        }

        function MyComponent() {
            return <div onClick={say_click}>
                <input />
                <input type="button"/>
            </div>
        }

state
---------------------------

``React.Component`` 内部维护了一个 state 状态，是一个字典。使用 ``this.setState`` 修改state中的值。
修改后，会自动更新UI界面。 state 可以通过 ``this.state`` 读取

props
---------------------------
``React.Component`` 可以接受一组参数。这组参数只读，无法修改。
通过 ``this.props`` 访问，是一个字典。

完整教程
===========================

了解上述概念后，按照下面的教程做一遍就知道了

中文版教程: https://react.docschina.org/tutorial/tutorial.html
装逼版教程: https://reactjs.org/tutorial/tutorial.html

没有比这讲的更详细的。
