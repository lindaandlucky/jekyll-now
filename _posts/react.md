# redux

Redux是一个用来管理管理数据状态和UI状态的JavaScript应用工具。随着JavaScript单页应用（SPA）开发日趋复杂，JavaScript需要管理比任何时候都要多的state（状态），Redux就是降低管理难度的。（Redux支持React，Angular、jQuery甚至纯JavaScript）

react是简单的视图层框架

Redux是数据层框架

```js
imrc     // 快速生成react和dom的引用
ccc      // 快速生成react组件代码
这些可以实现的前提是装有插件Simple React Snippets
```

工作流程：

reducer里只能接受state ,不能改变state

JSON.parse(JSON.stringify(state))可以深拷贝对象

写`Redux Action`的时候，我们写了很多Action的派发，产生了很多`Action Types`，如果需要`Action`的地方我们就自己命名一个`Type`,会出现两个基本问题：

- 这些Types如果不统一管理，不利于大型项目的服用，设置会长生冗余代码。
- 因为`Action`里的`Type`，一定要和`Reducer`里的`type`一一对应在，所以这部分代码或字母写错后，浏览器里并没有明确的报错，这给调试带来了极大的困难。

那我司中会把`Action Type`单独拆分出一个文件。在`src/store`文件夹下面，新建立一个`actionTypes.js`文件，然后把Type集中放到文件中进行管理。

只有一个store，只有store能改变自己的内容，reducer不能改变

纯函数就是返回的值完全是依赖传入的参数决定的。reducer必须接受纯函数，所以在这里是不能调用ajax的

多使用无状态组件，也就是纯ui组件，这样就可以提升性能

关于react-router的动态传值的步骤： 设置规则，传递值，接收值，显示内容

npm run eject弹出配置文件，可以自定义配置web pack,这个是不可逆的

扩展package.json里的scripts配置，扩展npm run 命令

## redux实现原理

createStore是redux的核心，它将所有的功能连接在一起，暴露可以操作的API

redux默认只处理同步，异步任务需要使用react-thunk中间件，步骤：

npm i redux-thunk  --save

使用applyMiddleware开启thunk中间件

action可以返回函数，使用dispatch提交action

React-redux的使用：

provider组件在应用最外层，传入store即可，只用一次

Connect 负责从外部获取组件需要的参数

Connect可以用装饰器的方式来写

如何使用装饰器来写呢？

npm run eject 弹出个性化配置

npm install babel-plugin-transform-decorators-legacy插件

Package.json里babel加上plugins配置

# 关于运营后台改造的知识点记录：

bizcharts.    react图表库   使用方式：https://www.jianshu.com/p/9dc63b4d96dd

npm（classnames） 更灵活使用类名      https://blog.csdn.net/cjg214/article/details/81125154

immutability-helper 这个工具来对原生JS对象进行操作。    https://www.jianshu.com/p/220e0271d2e4

Lodash是一个一致性、模块化、高性能的 JavaScript 实用工具库。

Memorize-one是一个性能优化的插件。   https://www.jianshu.com/p/b123bbe0330c

Moment.js是总结一个非常实用的日期工具类moment.js，日期获取，格式化等。

Numeral.js数字格式化.      https://blog.csdn.net/moakun/article/details/81807259

omitjs.     返回一个没有列入排除key属性的对象。其中，参数object为JSON格式的对象，*keys表示多个需要排除掉的key属性。      https://www.jianshu.com/p/ddc13a6f122a

path-to-regexp 介绍.         将路径字符串（如/ user /：name）转换为正则表达式。https://blog.csdn.net/weixin_33768153/article/details/82413983

Prop-types          在多人开发时，当被人使用自己定义的组件时，有可能出现类型传错的情况，而在自己的组件上加上prop-types，他可以对父组件传来的props进行检查，加入父组件中想传递的是字符串类型‘3’，而传递了一个数字类型3，如果没有类型检查系统不会给与提示，但是有了类型检查以后，再控制台会给你一个类型传递错误的提示。这样在工作中可以快速找到错误。    https://blog.csdn.net/sjpeter/article/details/81079619

qs是一个url参数转化（parse和stringify）的js库。

react-container-query.       媒体查询 响应式组件

React DnD 是一组 React 高阶组件，使用的时候只需要使用对应的 API 将目标组件进行包裹，即可实现拖动或接受拖动元素的功能。将拖动的事件转换成对象中对应状态的形式，不需要开发者自己判断拖动状态，只需要在传入的 spec 对象中各个状态属性中做对应处理即可。

React-document-titile.   可以实现在单页应用中根据不同路由来改变文档的title https://blog.csdn.net/qq_21901233/article/details/86593281

[webpack-theme-color-replacer](https://github.com/hzsrc/webpack-theme-color-replacer)插件，为[ant-design](https://github.com/ant-design/ant-design)实现了在运行时动态切换主题色的功能，无需在页面进行less的编译，提升了切换速度

useEffect可以替代副作用函数ComponentDidAmout he ComponentDidUpdate它是异步的，不会影响视图更新

# react-router

## 入门组件

BrowserRouter : 包裹整个应用

Router： 路由对应渲染的组件，可嵌套

Link：跳转专用

