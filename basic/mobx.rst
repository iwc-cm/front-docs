###########################
mobx
###########################

mobx 介绍
====================

mobx 是一个数据管理的 js 库。里面实现了观察者模式。

如果照着 React 基础教程写过一遍，可能觉得react的 state/props 比较美好。
实际应用在大型项目中，就不是那么回事了。因为组件嵌套的时候，父组件只能通过 props 传递数据到子组件。
而子组件又不能修改props，就算子组件将其保存为state，修改后，父组件也检测不到子组件做了什么修改，
因为父子组件不能交互。

比如做一个 可以自由展开树形结构，每一层每一个节点都是一个组件，一直递归，每个组件管理自己节点的数据。
当节点想要修改的时候，必须要顶层组件透传下来一个修改的函数，然后由顶层节点修改，再通过props传递到下层节点。


这时候，mobx就派上用场了，mobx可以将一个数据注册为 **被观察者** ，然后数据export给所有模块使用。

mobx 模型
============================

.. image:: /_static/mobx-model.jpg

mobx 实现了观察者模型，一个数据注册为 **被监视** 后, 可以被 **观察者** 监视。
被监视数据不能直接修改，只能通过 Action 修改。

总体上数据流是单向的。


mobx 使用
===========================

注册被监视数据
---------------------------

一般来说，同一个业务的数据存放到同一个 Store 类里面。通过 ``@observable`` 标记为被观察数据。

假设我们要实现统计按钮点击次数的功能，下面的例子注册一个按钮点击次数的被观察数据。然后 export 导出.

.. code-block:: javascript

    // store.ts
    import {observable} from 'mobx';

    class Store {
        @observable
        public clickNumber: number = 0;

        // 下面还可以继续使用 @observable 注册其他被监视数据。
        // ... ...
    }

    export default new Store();

编写 Action 
------------------------------

使用 ``@action`` 将函数标记为action, 用来修改 store 数据

.. code-block:: javascript

    // action.ts
    import {action} from 'mobx';
    import store from './store';

    class Action {
    
        @action
        public increaseClickNumber() {
            store.clickNumber += 1;
        }

        // 如果需要，下面还可以继续写其他 action 函数
        // ... ...
    }


在react中使用
-------------------------------

react组件需要使用 ``@observer`` 注册为观察者，否则数据改变后组件并不会自动更新。

然后react组件中就可以通过 store 使用数据，通过 action 修改数据了。

.. code-block:: typescript

    import * as React from 'react';
    import {observer} from 'mobx-react';
    import action from './action';
    import store from './store';

    @observer
    class MyComponent extends React.Component<any, any> {
        public render() {
            return <div>
                你已经点击了{store.clickNumber}次.
                <button onClick={()=>action.increaseClickNumber()}>猛击此处</button>
            </div>
        }
    }

请求服务器数据
================================

一般 action 中会请求远程服务器得到想要的数据。

介绍一下请求数据的方法 -- fetch。

发送get请求
------------------------

    ::

        fetch('/url')
            .then(req=>req.json())
            .then(data=>{
                // do something
            })

发送post请求
------------------------

    ::

        let postData = {name: "Jack"}

        fetch('/url', {
            method: 'post',
            body: JSON.stringify(postData),
            headers: {
                "Content-Type": "application/json"
            }
        })
            .then(req=>req.json())
            .then(data=>{
                // do something
            })
