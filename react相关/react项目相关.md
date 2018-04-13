#react
##一、使用npm初始化react项目

###1、关于package.json
	dependences 是项目正常运行所需要的依赖，而devDependencies则是开发者开发时整个项目所需的依赖（如会有一些测试依赖之类的）。

npm install


会默认安装两种依赖。

如果你只是单纯的想使用这个包而不需要进行一些改动测试之类的操作，则运行：（只安装dependencies而不安装devDependencies。）

npm install --production


如果想要安装devDependencies,则运行：

npm install packagename --dev 

###2.使用class方式创建组件时 要注意使用constructor方法初始化
class App extends Component{
constructor(props){
  super(props)
  this.state = {
    liked: props.initialValue
};
  this.handleClick = this.handleClick.bind(this);

}
getInitialState() {
  return {liked: false};
}
handleClick(event) {
  this.setState({liked: !this.state.liked});
}
render() {
  var text = this.state.liked ? 'like' : 'haven\'t liked';
  return (
    <p onClick={this.handleClick}>
      You {text} this. Click to toggle.
    </p>
  );
}
}
export default App;


必须将属性和方法绑定，否则不会生效

由于 this.props 和 this.state 都用于描述组件的特性，可能会产生混淆。 一个简单的区分方法是，this.props 表示那些一旦定义，就不再改变的特性， 而 this.state 是会随着用户互动而产生变化的特性。


###3、组件的生命周期和相应方法
组件的生命周期分成三个状态：

Mounting：已插入真实 DOM Updating：正在被重新渲染 Unmounting：已移出真实 DOM

React 为每个状态都提供了两种处理函数，will 函数在进入状态之前调用，did 函数在进入状态之后调用，三种状态共计五种处理函数。

componentWillMount()组件最初加载时被调用，只会执行一次<br>
 componentDidMount()执行一次<br>
 componentWillUpdate(object nextProps, object nextState)状态改变时执行<br>
 componentDidUpdate(object prevProps, object prevState)<br>
 componentWillUnmount()<br>
这五种方法不用在构造函数中绑定，直接调用即可

