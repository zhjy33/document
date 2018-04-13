#react-route
官方示例：
https://github.com/reactjs/react-router-tutorial/tree/master/lessons<br>
使用路由需要引入的类库
{"react": "^0.14.7",
    "react-dom": "^0.14.7",
    "react-router": "^2.0.0"}
import { Router, Route, hashHistory } from 'react-router'

语法:
`<Router history={hashHistory}>`<br>
`    <Route path="/" component={App}/>`<br>
`    {/* add the routes here */}`<br>
`    <Route path="/repos" component={Repos}/>`<br>
`    <Route path="/about" component={About}/>`<br>
 ` </Router>`<br>

配合Link组件实现跳转<br>
`<div>`<br>
`<Link to="/about">about</Link>`<br>
`                <Link to="/repos">repos</Link>`<br>
`           </div>`<br>
关于Route的中文文档http://react-guide.github.io/react-router-cn/<br>
<Route>可以嵌套
这时，加载内部组件之前会先加载外层组件
注意在组件中填入如下{this.props.children}<br>
