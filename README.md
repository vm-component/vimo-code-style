# Vimo-Style-Guide

此文档适用于编写基于Vimo的前端项目, 涵盖了JavaScript/Scss/Html/Vue四个部分.

## 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [{{Javascript}}](#javascript)
    - [使用严格模式](#%E4%BD%BF%E7%94%A8%E4%B8%A5%E6%A0%BC%E6%A8%A1%E5%BC%8F)
    - [引号](#%E5%BC%95%E5%8F%B7)
    - [行末分号](#%E8%A1%8C%E6%9C%AB%E5%88%86%E5%8F%B7)
    - [变量命名](#%E5%8F%98%E9%87%8F%E5%91%BD%E5%90%8D)
    - [其余命名方式](#%E5%85%B6%E4%BD%99%E5%91%BD%E5%90%8D%E6%96%B9%E5%BC%8F)
    - [缩进](#%E7%BC%A9%E8%BF%9B)
- [{{Scss}}](#scss)
  - [class命名(BEM)](#class%E5%91%BD%E5%90%8Dbem)
    - [[Block]](#block)
    - [[Element]](#element)
    - [[Modifier]](#modifier)
  - [id命名](#id%E5%91%BD%E5%90%8D)
  - [禁止使用无样式class来hook脚本](#%E7%A6%81%E6%AD%A2%E4%BD%BF%E7%94%A8%E6%97%A0%E6%A0%B7%E5%BC%8Fclass%E6%9D%A5hook%E8%84%9A%E6%9C%AC)
- [{{Html}}](#html)
    - [title的声明](#title%E7%9A%84%E5%A3%B0%E6%98%8E)
    - [页面&lt;h1&gt;标签唯一性](#%E9%A1%B5%E9%9D%A2lth1gt%E6%A0%87%E7%AD%BE%E5%94%AF%E4%B8%80%E6%80%A7)
    - [标签嵌套规则](#%E6%A0%87%E7%AD%BE%E5%B5%8C%E5%A5%97%E8%A7%84%E5%88%99)
- [{{Vue}}](#vue)
  - [Vimo模板](#vimo%E6%A8%A1%E6%9D%BF)
    - [组件的书写顺序](#%E7%BB%84%E4%BB%B6%E7%9A%84%E4%B9%A6%E5%86%99%E9%A1%BA%E5%BA%8F)
  - [Style部分](#style%E9%83%A8%E5%88%86)
  - [Html部分](#html%E9%83%A8%E5%88%86)
    - [1. 事件](#1-%E4%BA%8B%E4%BB%B6)
    - [2. 属性](#2-%E5%B1%9E%E6%80%A7)
      - [[this]](#this)
      - [[ref]](#ref)
      - [[_前缀]](#_%E5%89%8D%E7%BC%80)
      - [[props]](#props)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
## {{Javascript}}

> JavaScript代码的规范参考[Standard Code Style](https://github.com/feross/standard/blob/master/docs/README-zhcn.md) 
 
 JavaScript风格百家争鸣, 这里统一使用[Standard Code Style](https://github.com/feross/standard/blob/master/docs/README-zhcn.md), 其中Webstorm自带此规范, 且能自动修正不符合规范的地方, 较为方便. 
 
 
#### 使用严格模式

> 在代码中使用严格模式`'use strict';`，详细参考[javascript严格模式详解](http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)。

```javascript
'use strict';
arr1 = new Array();          // Error
var arr2 = new Array();      // Success
```

#### 引号
> js全部使用单引号`''`，拼html模板内使用双引号`""`。

```javascript
// bad
var param = "string";
var html = head + "<div class='main' data-id='main'></div>" + footer;

// good
var param = 'string';
var html = head + '<div class="main" data-id="main"></div>' + footer;
```

#### 行末分号
> 虽然js行末的分号不是必须的，但是为了代码风格统一，以及避免打包压缩带来的不可预测问题（真正会导致上下行解析出问题的token有5个：括号，方括号，正则开头的斜杠，加号，减号。一行开头是括号或者方括号的时候不添加分号会报错。），每行末的分号不可以省略。

> js分号工具[semi](https://github.com/yyx990803/semi)

```javascript
// bad
var html = head + "<div class='main' data-id='main'></div>" + footer
alert(html)

// error
var num = 1
(function() {
    console.log(num)
})
var str = 'error message'

// good
var html = head + '<div class="main" data-id="main"></div>' + footer;
alert(html);
```

#### 变量命名
> js变量命名使用小驼峰命名法，按照类型进行区分，需要突出属性特征、用途，不要使用不能清晰表达意义的缩略词。

- 普通对象

```javascript
// bad
var lib-name = 'sammy.js';
var lib_name = 'sammy.js';
var LibName  = 'sammy.js';

// good
var libName  = 'sammy.js';
```

- jQuery对象：`统一添加 $ 作为命名前缀，突出为jQuery对象`

```javascript
// bad
var slider   = $('#slider');
var side-bar = $('#sideBar');
var side_bar = $('#sideBar');

// good
var $slider  = $('#slider');
var $sideBar = $('#sideBar');
```

- 函数：`小驼峰写法，中间无中横线或者下横线`

```javascript
// bad
function get_name() {}
function get-name() {}

// good
function getName() {}
```

- 类(构造函数声明)：`首字母需要大写，驼峰写法`

```javascript
// bad
function superClass() {}

// good
function SuperClass() {}
```

- 缩写词需要准确表明意义

```javascript
// bad
var comm = document.getElementById('#comment');

// good
var comment = document.getElementById('#comment');
```

#### 其余命名方式

* `variableNamesLikeThis`
* `functionNamesLikeThis`
* `functionArgumentsLikeThis`
* `ClassNamesLikeThis`
* `EnumNamesLikeThis`
* `methodNamesLikeThis`
* `CONSTANTS_LIKE_THIS`
* `namespacesLikeThis`
* `private` or `protected` 属性和方法需要在前面加上`_`前缀
* 不应该使用短名称或者有歧义的名称
* 常用的缩略语, 比如 `JSON` 和 `XML`写成 `CamelCase`格式. 例如: `Json`, `Xml`.

#### 缩进
> `空格`与`tap`不能混用。如果使用`空格`，四个`空格`代替一个缩进的位置。如果使用`tap`，请设置一个`tap`代替四个`空格`的位置长度。

 

## {{Scss}}


> 建议项目全部使用Scss格式编写, 并且使用BEM的书写风格


### class命名(BEM)

建议采用OOCSS的思想编写样式文件, BEM是一个样式编写规范, 这里介绍了它的[命名规范](http://getbem.com/naming/). 简要的说, 其将一个元素或者结构分为三级结构:

- `block__element--modifier` 
- `block__element--modifier-other` 

因此, 按照规范, 编写及后续维护都将不再困难.

#### [Block]
- name

```
.block
```
- html

```html
<div class="block">...</div>
```
- css

```css
.block { color: #042; }
```

#### [Element]
- name

```
.block__elem
```
- html

```html
<div class="block">
	  ...
	<span class="block__elem"></span>
</div>
```
- css

```css
.block__elem { color: #042; }
```

#### [Modifier]
- name

```
// 一层修饰符
.block--mod 
.block__elem--mod 
 // 两层修饰符
.block--color-black 
.block--color-red.
```
- html

```html
<div class="block block--mod">...</div>
<div class="block block--size-big block--shadow-yes">...</div>
```
- css

```css
.block__elem--mod { }
```


### id命名
> 小驼峰写法，中间无中横线或者下横线。

```css
/* bad */
#Logo             { xxx }
#header_logo      { xxx }
#header-logo      { xxx }
#HeaderLogo       { xxx }

/* good */
#logo             { xxx }
#headerLogo       { xxx }
#headerLogoWrap   { xxx }
```

### 禁止使用无样式class来hook脚本
> 禁止为元素定义无样式的class，而作为调用脚本使用。这样会造成页面class定义冗余以及增加维护难度。请使用元素自带属性或自定义属性实现。

```html
// bad
<div class="click-alert"></div>
$('.click-alert').click(function() {});

// good
<div data-action="clickAlert"></div>
$('div[data-action="clickAlert"]').click(function() {});
```

## {{Html}}

> 使用`utf-8`编码方式，指定字符编码的`meta`必须是`head`的第一个子元素，[原因详解](http://www.qianduan.net/html5-charset-can-it/)。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        ...
    </hed>
    <body>
        ...
    </body>
</html>
```

#### title的声明
> `title`必须作为`head`的直接子元素，并紧随`charset`声明之后。`title`中如果包含`ascii`之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>标题</title>
        ...
    </hed>
    <body>
        ...
    </body>
</html>
```

#### 页面&lt;h1&gt;标签唯一性
> 一个页面只能有一个h1标签，具体与seo有关。

```html
<!-- bad -->
<h1>我是标题一</h1>
<h1>我是标题二</h1>

<!-- good -->
<h1>我是标题一</h1>
<h2>我是标题二</h2>
...
<h6>我是标题六</h6>
```

#### 标签嵌套规则
> html标签包含块级元素、内联元素，元素的类型决定嵌套的规则。

> 常见块元素：div、section、ul、li、p、h1~h6等。

> 常见内联元素：span、a、i、input、label、img等。

- 常见嵌套

```html
<!-- right：块级元素可以内嵌其他块级元素或者内联元素 -->
<div><h1><span></span></h1></div>

<!-- right：内联元素可以内嵌其他内联元素 -->
<a href=""><span></span></a>
```



- 错误嵌套

```html
<!-- wrong：内联元素不能嵌套其他块级元素 -->
<span><div></div></span>

<!-- wrong：p元素不能内嵌块级元素，类似元素有h1、h2、h3、h4、h5、h6、p、dt -->
<p><div></div></p>
<h1><div></div></h1>
...
<h6><div></div></h6>

<!-- wrong：a标签不能内嵌a标签，这个错误会经常发生，值得重视 -->
<a href="a.html"><a href="a.html"></a></a>
```


- 回退

```html
<!-- right：内联元素内嵌块级元素 -->
<a style="display: block;" href=""><div></div></a>
```


## {{Vue}}

`*.vue`文件是以上三者(JavaScript/Scss/Html)的组合, 使用规范雷同, 不同部分下面列出: 

### Vimo模板

```html
<template>
    <Page>
        <Header>
            <Navbar>
                <Title>Title</Title>
            </Navbar>
        </Header>
        <Content padding class="outer-content">
            <p>Content</p>
        </Content>
    </Page>
</template>
<style scoped lang="scss">

</style>
<script type="text/javascript">
  export default{
    name: 'name',
    data(){
      return {}
    },
    props: {},
    watch: {},
    computed: {},
    methods: {},
    created () {},
    mounted () {},
    activated () {},
    components: {}
  }
</script>

```

#### 组件的书写顺序
建议：template style script 的顺序书写

```html
<template></template>
<style></style>
<script></script>
```


### Style部分

- style中需要加上`scoped`属性标识css的作用域


### Html部分

> 使用简写模式结构比较清晰

```html
<!-- bad -->
<a v-on:click="pass()">pass</a>

<!-- good -->
<a @click="pass">pass</a>

### JavaScript部分

- script需要加上type类型, 因为Webstorm的自动格式化需要这个标记
- name属性必填, 便于Devtool的定位

```javascript
  import myComponentsA from './myComponentsA.vue'
  import myComponentsB from './myComponentsB.vue'
  import myComponentsC from './myComponentsC.vue'
  import myComponentsD from './myComponentsD.vue'
  export default {
    components: {
  	  myComponentsA,
      myComponentsB,
      myComponentsC,
      myComponentsD,
    }
  }
```


#### 1. 事件

事件绑定部分示例, 如果没有特殊的命名则使用对应格式的命名方式: 

- @click -> clickHandler
- @onSelect -> onSelectHandler

```html
<p @click="clickHandler">Content</p>
<Select @onSelect="onSelectHandler"><Select>
```

#### 2. 属性

##### [this]

 除非必须, 否则不缓存this变量, 作用域的问题使用箭头函数解决(=>)

##### [ref]

- 如果用ref获取组件实例, 需要在名称后面加`Component`, 例如`selectComponent`

```html
<template>
    <Select ref="select"></Select>
</template>
<script type="text/javascript">
export default {
    computed: {
  	  selectComponent(){
  	  	return this.$refs.select
  	  }
    }
}
</script>
```


- 如果用ref获取元素, 需要在名称后面加`Element`, 例如`selectElement `

```html
<template>
    <p ref="select">Hello</p>
</template>
<script type="text/javascript">
export default {
    computed: {
  	  selectElement(){
  	  	return this.$refs.select
  	  }
    }
}
</script>
```

##### [_前缀]

`_`前缀是内部变量, 不建议在vue文件中定义, 直接使用普通名称就好

##### [props]

在编写组件时, 有时需要缓存props值并进行修改, 比如props中的value需要修改, 缓存值可命名为theValue,  其他缓存的变量命名如下:

- value -> theValue
- disabled -> theDisabled
- duration -> theDuration
