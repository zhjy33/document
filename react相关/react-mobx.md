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