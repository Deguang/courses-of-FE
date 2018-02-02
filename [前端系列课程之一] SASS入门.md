title: [前端系列课程之一] SASS入门
speaker: 李德广
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css
"transition: zoomin
theme: moon

[slide]

# [前端系列课程之一] SASS入门
### 李德广

[slide]
[magic]
# Q1:什么是CSS？ {:&.rollOut}
# Q2:CSS 是一门编程语言吗？
====
* CSS，Cascading style sheets，层叠样式表，为结构化文档添加样式的的工具 {:&.flexbox.vleft}
* CSS不是一种编程语言, 不具备编程语言的特性，没有变量，没有函数，不支持表达式，没有嵌套、继承、宏 ... ...
====
 #### 这不是广告
 #### <p style="font-size: bold;">👇</p>
 <img src="http://p0.meituan.net/deal/__44963374__7636760.jpg" alt="举个例子">
 #### <p style="font-size: bold;">👆</p>
 #### 这个🌰霞姐选的
====
### css VS css
<img src="../vs.png" alt="css vs sass">
[/magic]

[slide]
# CSS预处理器 {:&.flexbox.vcenter}

[magic data-transition="rollIn"]

## CSS 预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为 CSS 增加了一些编程的特性，将 CSS 作为目标生成文件，然后开发者就只要使用这种语言进行编码工作。 {:&.rollIn,:&.flexbox.vleft}

==== {:&.flexbox.vleft}
## 常见CSS预处理器：

* SASS/SCSS. {:&.rollIn}
* LESS.
* Stylus.

* <a href="http://www.oschina.net/question/12_44255" target='_blank'>详细比较三个 CSS 预处理器（框架）：Sass、LESS 和 Stylus</a>
[note]
css预处理器，用于在页面开发中，优化CSS的编写体验，
通俗的说，“CSS 预处理器用一种专门的编程语言，进行 Web 页面样式设计，然后再编译成正常的 CSS 文件，以供项目使用。CSS 预处理器为 CSS 增加一些编程的特性，无需考虑浏览器的兼容性问题”，例如你可以在 CSS 中使用变量、简单的逻辑程序、函数（如右侧代码编辑器中就使用了变量$color）等等在编程语言中的一些基本特性，可以让你的 CSS 更加简洁、适应性更强、可读性更佳，更易于代码的维护等诸多好处。
[/note]
[/magic]

<!-- sass入门 -->
[slide]
<img src="http://sass-lang.com/assets/img/logos/logo-b6e1ef6e.svg" alt="sass" height="150px">
## {:&.rollIn}
## SASS是基于Ruby开发一种CSS的开发工具，提供了许多便利的写法，使得CSS的开发，变得简单和可维护。

<!-- sass 基础语法 -->
[slide]
# sass的安装

[magic]

## 1：安装Ruby {:&.flexbox.vleft}
### Mac 自带Ruby， 可进行update, windows 需自行下载ruby安装包安装；
```
$ gem update
```
====
## 2️：安装sass {:&.flexbox.vleft}
```
gem install sass
sudo gem install sass
sass -v
```
====
### PS: {:&.flexbox.vleft}
### 此处安装若遇到资源服务器连接失败等问题，可切换source到淘宝
```
$ gem sources -l  ＃查看当前镜像服务器
$ gem source --remove http://gems.github.com  ＃remove
$ gem source --add https://ruby.taobao.org/
```
### 若遇到```gem install sass```报以下错误
```
~ sudo gem install sass
    ERROR:  While executing gem ... (Errno::EPERM)
    Operation not permitted - /usr/bin/sass
```
### 可使用如下命令，修改安装目录
```
sudo gem install -n /usr/local/bin sass
```
====
## 3.编译Sass文件 {:&.flexbox.vleft}
### 编译sass -> css
```
$ sass test.scss
```
```
$ sass test.scss test.css
```
====
## 四种编译风格 {:&.flexbox.vleft}
* nested：嵌套缩进的css代码，它是默认值。
* expanded：没有缩进的、扩展的css代码。
* compact：简洁格式的css代码。
* compressed：压缩后的css代码。

```
sass --style compressed test.sass test.css
```
====
## Sass文件监控 {:&.flexbox.vleft}
```
// watch a file
sass --watch input.scss:output.css
// watch a directory
sass --watch app/sass:public/stylesheets
```
[/magic]

[slide]
# Sass 基本用法

[magic]

==== {:$.flexbox.vleft}
## 1.sass 文件后缀
### <p style="text-indent: 2em">fileName.sass</p>
### <p style="text-indent: 2em">fileName.scss</p>

## 区别：
### <p style="text-indent: 2em">语法书写方式不同，Sass 是以严格的<u>缩进式语法</u>规则来书写，不带大括号({})和分号(;)，而 SCSS 的语法书写和我们的 CSS 语法书写方式非常类似。</p>

==== <!-- sass／scss 对比 -->
###fileName.sass {:$.flexbox.vleft}
```css
$font-stack: Helvetica, sans-serif  //定义变量
$primary-color: #333 //定义变量
body
  font: 100% $font-stack
  color: $primary-color
```
###fileName.scss {:$.flexbox.vleft}
```css
$font-stack: Helvetica, sans-serif;
$primary-color: #333;
body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
###编译出来的 CSS {:$.flexbox.vleft}
```css
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```

==== {:$.flexbox.vleft}
## 2.变量
### Sass允许使用变量，变量以```$```开头
```css
$viColor: #6BD3CC

div {
　color: $viColor;
}
button{
  color: $viColor;
}
```
### 如果变量需要镶嵌在字符串之中，就必须需要写在```#{}```之中。
```css
$side : left;
.rounded {
　　border-#{$side}-radius: 5px;
}
```
==== {:$.flexbox.vleft}
## 3.算式
### Sass允许在代码中使用算式：
```css
$var: 100px;
body {
　margin: (14px/2);
　top: 50px + 100px;
　right: $var * 10%;
}
```

==== {:&.flexbox.vleft}
## 4.嵌套
### 选择器嵌套。比如，下面的CSS代码：
```css
div {
    font-size: 14px;
}
div h1 {
　　color : red;
}
div p {
    font-size: 14px;
}
```
### 用sass可以写成：
```css
div {
   font-size:14px;
　　h1 {
　　　　color:red;
　　}
    p {
       font-size: 14px;
    }
}
```
==== {:&.flexbox.vleft}
## 4.嵌套
### 属性也可以嵌套，比如border-color属性，可以写成：
```
p {
　　border: {
　　　　color: red;
　　}
}
```
#### 属性嵌套，例如border后面必须加上冒号。
### 在嵌套的代码块内，可以使用&引用父元素。比如a:hover伪类，可以写成：
```
a {
　　&:hover { color: #ffb3ff; }
}
```
==== {:&.flexbox.vleft}
## 5.注释
###SASS共有两种注释风格。
### 标准的CSS注释 ```/* comment */``` ，会保留到编译后的文件。
### 单行注释 ```// comment```，只保留在SASS源文件中，编译后被省略。
### 在```/*```后面加一个感叹号，表示这是"重要注释"。即使是压缩模式编译，也会保留这行注释，通常可以用于声明版权信息。
```css
/*!
　　重要注释！
*/
```
==== {:&.flexbox.vleft}
### ps:
#### 若注释出现在css不允许出现注释的地方，依然会被省略；
```css
$viColor: #6BD3CC;
input {
    color: /* comment */ $viColor;
}
```
####  👇👇👇👇👇
```
input {
    color: #6BD3CC
}
```
[/magic]

[slide]
# Sass 进阶用法

[magic]
## 1.代码重用－继承 {:&.flexbox.vleft}
### SASS允许一个选择器，继承另一个选择器。比如，class2要继承class1，就要使用```@extend```命令：
```css
.class1 {
　　border: 1px solid #ddd;
}

.class2 {
　　@extend .class1;
　　font-size:120%;
}
```
####  👇👇👇👇👇
```css
.class1, .class2 {
  color: #ccc; }

.class2 {
  font-size: 120%; }
```
==== {:&.flexbox.vleft}
## 2.代码重用－Mixin
### 可以重用的代码块。
### 使用```@mixin```命令，定义一个代码块;使用```@include```命令，调用这个mixin。

```
@mixin left {
　float: left;
　margin-left: 10px;
}

div {
　　@include left;
}
```
####  👇👇👇👇👇
```css
div {
    float: left;
    margin-left: 10px;
}
```
==== {:&.flexbox.vleft}
## 2.代码重用－Mixin
### mixin的强大之处，在于可以指定参数和缺省值。
```css
@mixin left($value: 10px) {
　　float: left;
　　margin-right: $value;
}
```
### 使用的时候，根据需要加入参数：
```css
div {
　　@include left(20px);
}
```
==== {:&.flexbox.vleft}
## 2.代码重用－Mixin
### mixin的实例，用来生成浏览器前缀。
```css
@mixin rounded($vert, $horz, $radius: 10px) {
　　border-#{$vert}-#{$horz}-radius: $radius;
　　-moz-border-radius-#{$vert}#{$horz}: $radius;
　　-webkit-border-#{$vert}-#{$horz}-radius: $radius;
}
```
调用：
```css
#navbar li {
  @include rounded(top, left);
}
#footer {
  @include rounded(top, left, 5px);
}
```
==== {:&.flexbox.vleft}
## 3 颜色函数
### SASS提供了一些内置的颜色函数，以便生成系列颜色。
```css
lighten(#cc3, 10%) // #d6d65c
darken(#cc3, 10%) // #a3a329
grayscale(#cc3) // #808080
complement(#cc3) // #33c
```

==== {:&.flexbox.vleft}
## 4 插入文件
### ```@import```命令，用来插入外部文件。
```css
@import "path/filename.scss";
```
### 如果插入的是.css文件，则等同于css的import命令。
```css
@import "foo.css";
```
[/magic]

[slide]
# Sass高级用法
[magic]
## 1.条件语句 {:&.flexbox.vleft}
### @if可以用来判断：
```css
p {
　　@if 1 + 1 == 2 { border: 1px solid; }
　　@if 5 < 3 { border: 2px dotted; }
}
```
### 配套的还有@else命令：
```css
@if lightness($color) > 30% {
　　background-color: #000;
} @else {
　　background-color: #fff;
}
```
==== {:&.flexbox.vleft}
## 2.循环语句
#### for循环：
```css
@for $i from 1 to 10 {
　　.border-#{$i} {
　　　　border: #{$i}px solid blue;
　　}
}
```
#### while循环：
```css
$i: 6;
@while $i > 0 {
　　.item-#{$i} { width: 2em * $i; }
　　$i: $i - 2;
}
```
#### each，作用与for类似：
```css
@each $member in a, b, c, d {
　　.#{$member} {
　　　　background-image: url("/image/#{$member}.jpg");
　　}
}
```
==== {:&.flexbox.vleft}
## 3 自定义函数
```css
@function double($n) {
　　@return $n * 2;
}
#sidebar {
　　width: double(5px);
}
```

[/magic]

[slide]
# Compass
[magic] {:&.flexbox.vleft}
* Compass是Sass的工具库（toolkit） {:&rollIn}
* Sass本身只是一个编译器，Compass在它的基础上，封装了一系列有用的模块和模板，补充Sass的功能。它们之间的关系，有点像Javascript和jQuery、Ruby和Rails、python和Django的关系

## reset使用： {:rollOut}
```css
@import "compass/reset";
```
### 这样就会在css中生成重置样式了，不用我们再自己定义重置样式了。

## css3使用：
```css
@import "compass/css3";
```
==== {:&.flexbox.vleft}
###由于浏览器对css3支持的差异性，我们很多时候需要写一堆针对不同浏览器前缀样式，着实很烦人，css3命令模块帮我们解决了这个问题，我们只需include相应样式定义即可，compass会自动为我们生成针对不同浏览器的样式定义：
```css
@import "compass/css3";
　.circle {
　　　@include border-radius(5px);
　}
```
####   👇👇👇👇👇
```css
.circle {
　　-moz-border-radius: 5px;
　　-webkit-border-radius: 5px;
　　-o-border-radius: 5px;
　　-ms-border-radius: 5px;
　　-khtml-border-radius: 5px;
　　border-radius: 5px;
}
```
[/magic]
[slide]
# Sass 在当前开发环境中的部署

<a href="javascript:void(0);" target="_blank">Wiki：sass环境搭建</a>


[slide]
## 抛砖引玉
