#react-mobx
mobx中文文档
http://cn.mobx.js.org/best/decorators.html<br>
注意， mobx-react 中的 observer 函数既是装饰器又是函数，这意味着下面这些语法都可以正常运行:

@observer
class Timer extends React.Component {
    /* ... */
}

const Timer = observer(class Timer extends React.Component {
    /* ... */
})

const Timer = observer((props) => (
    /* 渲染 */
))

不要把 computed 和 autorun 搞混。它们都是响应式调用的表达式，但是，如果你想响应式的产生一个可以被其它 observer 使用的值，请使用 @computed，如果你不想产生一个新值，而想要达到一个效果，请使用 autorun。 举例来说，效果是像打印日志、发起网络请求等这样命令式的副作用。

computed只能计算被观察的属性<br>
如果你有一个函数应该自动运行，但不会产生一个新的值，请使用autorun。 其余情况都应该使用 computed