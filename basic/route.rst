###########################
route 路由
###########################

如果只会用 React 写个单页面应用，没有任何跳转，也算不得什么英雄好汉。

基本原理
==================

JavaScript中通过 window.location 可以访问当前页面的 url 。

假设我们现在有三个页面

* TreeList: 显示植物列表
* TreeDetail: 显示植物详情
* Home: 主页

为了在 React 中根据不同的url显示不同内容。可以像下面一样写。

.. code-block:: typescript

    class Index extends React.Component<any, any> {
        render() {
            if (window.location.pathname == "/treeList") {
                return <TreeList />
            } else if (window.location.pathname == "/treeDetail") {
                return <TreeDetail />
            } else {
                return <Home />
            }
        }
    }

上面的代码也能工作，不过适用场景有限，社区已经有了更完善的 ``react-router`` 。

react router
=================================

上面的代码改写为 react router 路由代码就是下面的。

.. code-block:: typescript

    import React from 'react'
    import { BrowserRouter, Route, Link } from 'react-router'

    React.render((
        <BrowserRouter>
            <Route exact={true} path="/" component={Home} />
            <Route path="/treeList" component={TreeDetail} />
            <Route path="/treeDetail" component={TreeList} />
        </BrowserRouter>
    ), document.body)

注意 BrowserRouter 只能有一个，放在最外层，下面的 Route 可以有很多个，而且可以嵌套多层。

其中，exact表示url是否完全匹配，默认是前缀匹配，path 表示匹配到什么url，component表示匹配成功后渲染什么组件。

通过 Route 渲染的组件，会具有 ``this.props.history`` 和 ``this.props.match`` , 通过 this.props.history.push() 跳转到其他页面

::

    this.props.history.push("/treeList") 

具体接口看官方文档： https://reacttraining.com/react-router/web/guides/quick-start

中文教程: 

    * https://www.jianshu.com/p/548674270455
    * https://segmentfault.com/a/1190000014294604
