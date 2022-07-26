# Flow 介绍

flow 是 JavaScript 的静态类型检查器。弥补了一些 JavaScript 类型系统的一些弊端。

目前的 react.js 和 vue.js 项目中，都可以看到 flow 的使用。

## flow 工作原理

在代码中通过添加`类型注解`的方式，来标记代码当中每个变量应该是什么数据类型的。flow 这个工具会根据`类型注解`检查代码中是否存在语法层面的类型场景的异常。 从而实现在开发阶段检查出类型异常，而不需要运行代码了。

###### 类型注解的使用

```js
// 表示这个sum函数只能接受 两个 mumber 类型的数值；如果传入其他类型，会直接在编辑器里标红提示（语法层面提示）
function sum ( a`: number`, b `: number`) {
    return a + b
}
```

代码运行时，时不存在类型注解相关内容的，  在代码运行之前，会通过 babel 或者 flow 官方提供的模块自动去除掉类型注解相关的内容。

flow 并不要求我们给每一个变量都加上类型注解。

## 项目中使用flow的流程

1. flow 是以npm模块的方式去工作的，所以我们使用 `yarn init --yes`命令初始化一个`package.json `用来管理我们的依赖

2. 使用  `yarn add flow-bin --dev` 命令，安装开发依赖 （因为只有开发过程有用到 flow）

3. 在js文件中使用flow，需要在文件第一行加上  `// @flow` ,这样flow这个模块才会检查这个文件。

4. 但是这样设置之后，加了类型注解之后，发现代码还是有标红，这是因为vscode有自动的JavaScript代码校验规则，JavaScript代码校验规则事不支持类型注解这样的写法的。所以我们要关闭JavaScript代码校验规则。 `设置 -> javascript validate  `

5. 使用 `yarn flow init ` 初始化一个flow的配置文件，之后可以在终端中使用`yarn flow`命令执行代码检查，检查结果还是输出在终端中。

