# 第 1 章　什么是JavaScript

## JavaScript由三部分组成

万维网联盟（W3C，World Wide Web Consortium）制定了这些规范；

注意我们常说的JS标准，ES标准，其实是一个指导规范；然后由浏览器厂商和开发者进行支持。

一个完整的javascript实现应该有下列三个不同部分组成：

- 核心（ECMAScript）
- 文档对象模型（DOM）
- 浏览器对象模型（BOM）

![https://a.axihe.com/img/api/jses/js-set.png](https://a.axihe.com/img/api/jses/js-set.png)

- `ECMAScript`：提供核心语言功能,是核心，规定了这们语言的书写规范；

    ```
    let axihe="阿西河前端教程";
    ```

- `DOM`：提供访问和操作网页内容的方法和接口,(document object model 简称DOM 文档对象模型)

    ```
    var oDiv=document.getElementById("div1");
    oDiv.innerText="现在已经被我占领了";
    ```

- `BOM`：提供与浏览器交互的方法和接口；BOM最蛋疼的部分是没有统一的标准；从根本上讲BOM只处理浏览器窗口和框架,(browser object model 简称 BOM 浏览器对象模型)

    ```
    windows.location.href
    ```

## 浏览器支持

大多数浏览器对JavaScript的支持，指的是实现ECMAScript和DOM的程度；

BOM相对就比较随意，事实上是浏览器各自搞自己的。

## 一，ECMAScript

**ECMAScript**，提供核心语言功能,是核心，规定了这们语言的书写规范；

`ECMAScript`又简称`ES`，我们常说的JS语法指的是ECMAScript规定的语法；

注意：虽然我们前端主要在浏览器这里折腾，但是JSECMAScript 并不局限于Web浏览器。

Web浏览器只是ECMAScript的宿主之一，它还有别的宿主，比如目前基于ECMAScript的Node.js。

### ECMAScript版本

我们当前使用最基础的是ECMAScript5，这个在当前属于最基础的技能；

每年W3C都会对JavaScript进行新一版的规范制作，目前已经出来了ECMAScript2020啦，也就是ES11；

如果你对这些感兴趣，可以参考本站的 [ECMAScript 2020 文档](https://www.axihe.com/api/js-es/api/api.html)

#### ES6

ECMA-262第6版，俗称ES6、ES2015，于2015年6月发布。

这一版包含了大概这个规范有史以来最重要的一批增强特性。ES6正式支持了下面

- 类、
- 模块、
- 迭代器、
- 生成器、
- 箭头函数、
- 期约、
- 反射、
- 代理和众多新的数据类型。

#### ES7

ECMA-262第7版，也称为ES7或ES2016，于2016年6月发布。

这次修订只包含少量语法层面的增强，如

- `Array.prototype.includes`
- 指数操作符。

#### ES8

ECMA-262第8版，也称为ES8、ES2017，完成于2017年6月。

这一版主要增加了

- 异步函数（`async`/`await`）、
- `SharedArrayBuffer`及
- Atomics API，
- `Object.values()`
- `Object.entries()`
- `Object.getOwnPropertyDescriptors()`
- 字符串填充方法

另外明确支持对象字面量最后的逗号。

#### ES9

ECMA-262第9版，也称为ES9、ES2018，发布于2018年6月。

这次修订包括

- 异步迭代、
- 剩余和扩展属性、
- 一组新的正则表达式特性、
- `Promise finally()`，
- 模板字面量修订。

#### ES10

ECMA-262第10版，也称为ES10、ES2019，发布于2019年6月。

这次修订增加了
- `Array.prototype.flat()`
- `flatMap()`
- `String.prototype.trimStart()`
- `trimEnd()`
- `Object.fromEntries()`
- `Symbol.prototype.description`
- 明确定义了`Function.prototype.toString()`的返回值
- 固定了`Array.prototype.sort()`的顺序
- 解决了与JSON字符串兼容的问题
- 定义了`catch`子句的可选绑定。

#### ES11

ECMA-262第11版，也称为ES11、ES2020，发布于2020年6月。

ES2020中新的JavaScript特性包括:

* String.prototype.matchAll
* import()
* BigInt
* Promise.allSettled
* globalThis
* for-in mechanics
* Nullish coalescing Operator
* Optional Chaining

后续的规范可以在官网看看

官网地址: <https://www.ecma-international.org/publications/standards/Ecma-262.htm>


## 二，DOM

DOM全称`Document Object Model`,中文翻译是**文档对象模型**。

HTML页面，通过DOM将整个页面抽象为一组分层节点，借助DOM提供的API，可以轻松的增删改查；

下面是一个 `.html` 代码

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>这是显示在浏览器选项卡上的文字标题</title>
</head>
<body>
  <div id="page">您好啊，我是HTML</div>
</body>
</html>
```

关系解释如下

```
<!DOCTYPE html>
<html>
  <head>
    <!--meta标签是head的儿子，是title的哥哥-->
    <meta charset="UTF-8">
    <!--titles head的儿子，是meta的弟弟-->
    <title>这是显示在浏览器选项卡上的文字标题</title>
  </head>
  <!--body标签是html的儿子，是head的弟弟，是id=page这个div的父亲-->
  <body>
    <!--div标签是body的儿子-->
    <div id="page">您好啊，我是HTML</div>
  </body>
  <!--html是head和body的父亲-->
</html>
```

### DOM的优点

- 借助提供的API，可以轻松的增删改查
- 借助DOM做到不刷新页面而修改页面外观和内容 

### DOM级别

我们常说的DOM2级事件,就是指DOM的第二个级别；DOM分为好几个级别；

* DOM1的目标是映射文档结构
    - 有些文档会说DOM0,是指DOM规范出来的起点，我们一般看作是DOM1就可以了；
    - 我们主要是学习技术，这些严格的名词归属，其实并没有那么重要的；
* DOM2新增了以下模块，以支持新的接口。
    - **DOM视图**：描述追踪文档不同视图（如应用CSS样式前后的文档）的接口。
    - **DOM事件**：描述事件及事件处理的接口。
    - **DOM样式**：描述处理元素CSS样式的接口。
    - **DOM遍历和范围**：描述遍历和操作DOM树的接口。
* DOM3增加了
    - 以统一的方式加载和保存文档的方法
    - 验证文档的方法
* DOM4新增
    - 替代`Mutation Events`的`Mutation Observers`。 
    - 目前，W3C不再按照Level来维护DOM了，而是作为DOM活跃标准来维护，它的快照，我们称为DOM4。

## 三，BOM

BOM全称`Browser Object Model`,中文翻译是**浏览器对象模型**。

我们通常会把任何特定于浏览器的扩展都归在BOM的范畴内。比如，下面就是这样一些扩展：

- 弹出新浏览器窗口的能力；
- 移动、缩放和关闭浏览器窗口的能力；
- `navigator`对象，提供关于浏览器的详尽信息；
- `location`对象，提供浏览器加载页面的详尽信息；
- `screen`对象，提供关于用户屏幕分辨率的详尽信息；
- `performance`对象，提供浏览器内存占用、导航行为和时间统计的详尽信息；
- 对 `cookie` 的支持；
- 其他自定义对象，如`XMLHttpRequest` 和IE的`ActiveXObject`。

因为在很长时间内都没有标准，所以每个浏览器实现的都是自己的BOM。有一些所谓的事实标准，比如对于`window`对象和`navigator`对象，每个浏览器都会给它们定义自己的属性和方法。

## 本章小结

JavaScript是一门用来与网页交互的脚本语言，包含以下三个组成部分。

- **ECMAScript**
    - 定义JavaScript这门语言的语法规范
- **DOM**（文档对象模型）
    - 提供与网页内容交互的方法和接口。
- **BOM**（浏览器对象模型）
    - 提供与浏览器交互的方法和接口。

JavaScript的这三个部分得到了所有浏览器的支持，虽然支持的程度不同，但是支持度肯定是不断提升的。

因为这些是大家公认的规范，只要规范不瞎搞，开发者会一直接受，浏览器厂商也会支持；
