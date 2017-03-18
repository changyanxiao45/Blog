# React入门
## 安装
创建一个单页应用，通过[ create-react-app ](https://github.com/facebookincubator/create-react-app)来创建，创建命令如下
	npm install -g create-react-app
	create-react-app hello-world
	cd hello-world
	npm start

主要依赖[webpack](https://webpack.js.org/), [Babel](http://babeljs.io/) and [ESLint](http://eslint.org/)。



## JSX
在写JSX为了便于阅读通常会考虑换行，此时为了避免[ automatic semicolon insertion.](http://stackoverflow.com/questions/2846283/what-are-the-rules-for-javascripts-automatic-semicolon-insertion-asi),通常会在外层加入括号。
	const element = (
	  <h1>
	    Hello, {formatName(user)}!
	  </h1>
	);




## Components and Props(组建和属性)
All React components must act like [pure functions](https://en.wikipedia.org/wiki/Pure_function "纯函数") with respect to their props.(React组建不允许改变属性值)。



## State and Lifecycle(状态和生命周期)
### 钟表创建过程如下
1.ReactDOM.render()开始，当Clock被传入该方法时，将调用Clock组件的构造方法。此处设置state为当前时间（初始化）。
2.这之后将调用组件的render()函数，这将告诉react什么内容将显示。此时Reactj将返回内容更新到Dom。
3.当Clock内容插入Dom后，React调用componentDidMount()生命钩子。该方法内每隔一秒调用一次函数tick()
4.每一秒调用tick()方法时，Clock组件通过setState改变state值，React通过监听state的变化去调用Clock组件的render()方法。然后就变化的时间显示到屏幕上。
5.当Clock组件被移除时，React调用componentWillUnmount()生命钩子。
![](/images/Clock.png)
### 注意事项
1.不要直接去改变state的值。
2.state有时候更新是异步的，所以不要用当前的state去更新state。
3.state属性之间更新不受影响。
4.数据是从上往下的，组件一般作为属性值传递给下层属性，影响子组件。



## Handling Events
### 事件绑定
1.在构造方法中手动绑定this对象
	constructor(props) {
	    super(props);
	    this.state = {isToggleOn: true};

	    // This binding is necessary to make `this` work in the callback
	    this.handleClick = this.handleClick.bind(this);
	}
2.property initializer syntax(草案)，需引入[babel-plugin-transform-class-properties](https://babeljs.io/docs/plugins/transform-class-properties/)
	handleClick = () => {
	    console.log('this is:', this);
	}
3.在回调函数中使用箭头函数
	<button onClick={(e) => this.handleClick(e)}>
	    Click me
	</button>



## Lists and Keys
1.列表元素需要提供一个key值作为唯一标识。
2.健值只有在包含它的数组上下文中使用才有意义。
3.健值作为一个线索给React使用，但是它不会作为属性传递到属性中，在组件中是访问不到的。



## Forms
1.在React中,input,textarea,select都是通过 value属性来设置显示值。
2.如果需要控制多个input元素，则一般通过添加name属性作区分。



## Lifting State Up
当多个组件公用一个变化数据时，我们通常会将其提取到最近的父节点中。
Calculator执行过程
![](/images/2-1.png)
总结：
在React应用中，对于所有变化的数据都需要有一个唯一的数据源。通常state都是定义在第一次使用到它的组件中，当又有其他组件需要用到它时，我们将它提取到最近的父级组件中。我们通过从上到下数据流的方式来同步state，而不去在组件间同步。
这种方式，相对于独立绑定两个组件，可能要写更多的引用代码。但好处是，我们可以花更少的时间去解决关联问题。因为状态虽然绑定在多个组件中，但是能够改变它数值的组件只有一个，这样发生问题的区域就减小了很多，也就更容易定位问题。另外，你也可以实现一些共有逻辑来处理用户输入。
如果某个内容既可以从属性，又可以从状态获取，那么可能不应该放在state中。例如，我们存储最后一次编辑的value和scale，而不是存储celsiusValue和fahrenheitValue。另一个输入框的值可以通过它们计算得到。这让我们能够在不丢失精度的前提下清空和四舍五入另一个输入框内容。
最后，我们可以通过[React Developer Tools](https://github.com/facebook/react-devtools)来排查错误。

## Composition vs Inheritance
通过Composition来在组件之间复用代码。
