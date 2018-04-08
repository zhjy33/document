#react
##一、使用npm初始化react项目

###1、安装配置npm工具
###2、命令行输入 npx create-react-app 'app名称',名称不能包含大写
###3、进入项目目录   使用 npm/yarn start即可启动
###4、npm更新依赖   npm build更新项目依赖
###5、创建react组件
####1、创建组件的方式
1）、无状态组件
	无状态函数式组件形式上表现为一个只带有一个render方法的组件类，通过函数形式或者ES6 arrow function的形式在创建，并且该组件是无state状态的。具体的创建形式如下：

function HelloComponent(props, /* context */) {return <div>Hello {props.name}</div>
}<br>
ReactDOM.render(<HelloComponent name="Sebastian" />, mountNode) <br>

2）、React.createClass方式（不推荐）<br>

3)、React.Component（推荐使用）<br>


##二、使用react
###1、react的三种状态
组件的生命周期分成三个状态：

        Mounting：已插入真实 DOM
        Updating：正在被重新渲染
        Unmounting：已移出真实 DOM

React 为每个状态都提供了两种处理函数，will 函数在进入状态之前调用，did 函数在进入状态之后调用，三种状态共计五种处理函数。


        componentWillMount()
        componentDidMount()
        componentWillUpdate(object nextProps, object nextState)
        componentDidUpdate(object prevProps, object prevState)
        componentWillUnmount()

此外，React 还提供两种特殊状态的处理函数。

        componentWillReceiveProps(object nextProps)：已加载组件收到新的参数时调用
        shouldComponentUpdate(object nextProps, object nextState)：组件判断是否重新渲染时调用

##三、mobx和react结合
###1、链接如下https://segmentfault.com/a/1190000010084073
Mobx 的理念非常简单，可以用一个 demo 就把其核心原理说清楚。Mobx/MobxReact 中有三个核心概念，observable、observer、action。为了简单起见，本文没有提及 computed 等概念。

    observable: 通过 observable(state) 定义组件的状态，包装后的状态是一个可观察数据（Observable Data）。

    observer: 通过 observer(ReactComponent) 定义组件。

    action: 通过 action 来修改状态。


observable

	Mobx 如此简单的原因之一，就是使用了可观察数据(Observable Data)。简单说，可观察数据就是可以	观察到数据的读取、写入，并进行拦截。<br>

react系列介绍:segmentfault中的《React从入门到精通系列》<br>


链接https://segmentfault.com/search?q=React%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E7%B3%BB%E5%88%97