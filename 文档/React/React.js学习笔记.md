# React.js学习笔记

## 一. HTMl模版

```
<!DOCTYPE html>
<html>
  <head>
    <script src="../build/react.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    //<script> 标签的 type 属性为 text/babel,React 独有的 JSX 语法，跟 JavaScript 不兼容
    <script type="text/babel">
      // ** Our code goes here! **
    </script>
  </body>
</html>
```

## 二.ReactDOM.render()

## props和State

* 属性(props)是由父组件传递给子组件的
* 状态(state)是子组件内部维护的数据，当状态发生变化的同时，组件也会进行更新

## Webpack

Webpack 是一个前端资源加载/打包工具，只需要相对简单的配置就可以提供前端工程化需要的各种功能，并且如果有需要它还可以被整合到其他比如 Grunt / Gulp 的工作流。

安装：

```
npm install -g webpack
```

Webpack使用一个名为 webpack.config.js 的配置文件，要编译 JSX，先安装对应的 loader

```
npm install babel-loader --save-dev
```

webpack.config.js的配置（如果配置了这项，就只需执行webpack命令，就可以讲js文件转换为bundle.js文件，无需像以前一样在命令行中输入这两个参数）

```
module.exports = {
  entry: './public/app.jsx',
  output: {
    path: __dirname,
    filename: './public/bundle.js'
  },
  //resolve 指定可以被 import 的文件后缀。
  //比如 Hello.jsx 这样的文件就可以直接用 import Hello from 'Hello' 引用
  resolve: {
    extensions: ['', '.js', '.jsx']
  },
  module: {
    loaders: [
      {
      //编译 JSX
        loader: 'babel-loader',
        query: {
          presets: ['react', 'es2015']
        },
        test: /\.jsx?$/,
        exclude: /(node_modules|bower_components)/
      }
    ]
  }
};
```

React快的原因是引入虚拟DOM技术，不直接操作真实DOM对象，React将DOM结构存储在内存中，将其与render() 返回虚拟DOM的内容进行diff算法比较，计算出需要改动的地方，最后才反应到DOM中。


## React—组件生命周期详解

提供如下API供调用:

* componentWillMount()
* componentDidMount()
* componentWillUpdate(object nextProps, object nextState)
* componentDidUpdate(object prevProps, object prevState)
* componentWillUnmount()
* componentWillReceiveProps(object nextProps)：已加载组件收到新的参数时调用
* shouldComponentUpdate(object nextProps, object nextState)：组件判断是否重新渲染时调用
* 
1.实例化：

getDefaultProps：对于组件来说，这个方法只会调用一次，对于那些没有父辈组件指定的props属性的新建实例来说，这个方法返回的对象可用与为实例设置默认的props值

getInitalState：对于组件的每个实例来说，这个方法调用次数有且仅有一次，这里你将有机会初始化每个实例的state,与getDefaultProps方法不同的是，每次实例创建时该方法都会被调用一次，这个方法中，可以访问到this.props

componentWillMount：该方法在完成***首次***渲染之前被调用，这也是在render方法调用前可以修改组件state的最后一次机会

render：

在这里你创建一个虚拟DOM，用来表示组件的输出，对于一个组件来说，render是唯一一个必需的方法

componentDidMount：在***首次***render方法成功调用并且真实的DOM已经被渲染之后

![](http://chuantu.biz/t5/42/1479690164x988815626.png)

2.属性改变


![](http://chuantu.biz/t5/42/1479690276x988815626.png)


3.状态改变

![](http://chuantu.biz/t5/42/1479690342x988815626.png)


