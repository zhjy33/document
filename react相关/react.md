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


渲染元素：实际上，大多数React应用程序只调用ReactDOM.render()一次。 在接下来的章节中，我们将学习如何将这样的代码封装成有状态的组件。
React DOM将元素及其子元素的内容与该元素变化之前的内容进行比较，并仅进行DOM更新以使DOM达到所需的状态。
您可以通过使用浏览器工具检查最后一个示例来验证。
即使我们在每个tick上创建一个描述整个UI树的元素，只有内容发生改变的文本节点才被React DOM更新。

在我们的经验中，思考UI应该如何更新给定的时间，而不是随着时间的更改去修改整体的内容(DOM比较，按需更新)



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

##四、组件
###1、有状态组件
class InputControlES6 extends React.Component {
    constructor(props) {
        super(props);

        // 设置 initial state
        this.state = {
            text: props.initialValue || 'placeholder'
        };

        // ES6 类中函数必须手动绑定
        this.handleChange = this.handleChange.bind(this);
    }。。。此种方式创建的为有状态组件
###2、const myComponent = (props) =>{
    return(
        <div>Hello {props.name}</div>;
    );
}
无状态组件


React.createClass和React.Component都是创建有状态的组件，
这些组件是要被实例化的，并且可以访问组件的生命周期方法。


整体渲染性能得到提升
    因为组件被精简成一个render方法的函数来实现的，
    由于是无状态组件，所以无状态组件就不会在有组件实例化的过程，
    无实例化过程也就不需要分配多余的内存，从而性能得到一定的提升。
组件不能访问this对象
    无状态组件由于没有实例化过程，所以无法访问组件this中的对象，
    例如：this.ref、this.state等均不能访问。若想访问就不能使用这种形式来创建组件
组件无法访问生命周期的方法
    因为无状态组件是不需要组件生命周期管理和状态管理，
    所以底层实现这种形式的组件时是不会实现组件的生命周期方法。
    所以无状态组件是不能参与组件的各个生命周期管理的。
无状态组件只能访问输入的props，
    同样的props会得到同样的渲染结果，不会有副作用

无状态组件不能使用this关键字
