---
title: 关于 CSS margin，你需要知道的一切
tags: web前端开发-文章介绍
categories: web前端开发
abbrlink: 27168
date: 2019-07-31 13:14:52
---

原文：[https://juejin.im/post/5d40dc46e51d4561cf15df4a](https://juejin.im/post/5d40dc46e51d4561cf15df4a)

转载：Hani

---

# 简介

margin 看起来是一个相当简单的事情，但是，在本文中，咱们将看一些在使用 margin 一些让人迷惑有有趣的事情。 特别是，margin 之间如何相互作用，以及 margin 重叠效果。

# margin 重叠

margin 重叠意味着，当一个有底部 margin 的标题后面跟着一个有顶部 margin 的段落时，它们之间就不会出现较大的空白。

当两个 margin 发生重叠时，它们将组合在一起，两个元素之间的空间取较大的一个。 较小的 margin 在较大的里面。

在以下情况下，margin 会重叠：

- 相邻的兄弟姐妹
- 完全空盒子
- 父元素和第一个或最后一个子元素

依次来看看这些场景。

# 相邻的兄弟姐妹

对 margin 重叠的最初描述是演示相邻兄弟姐妹之间的 margin 是如何重叠的。除了下面提到的情况之外，如果有两个元素在正常流中依次显示，那么第一个元素的底部 margin 将与下面元素的顶部 margin 一起重叠。

在下面示例中，有三个 div 元素。第一个 div 的顶部和底部的 margin 都是 50px。第二个 div 的顶部和底部 margin 都是 20px。第三个 div 的顶部和底部 margin 都是 3em。前两个元素之间的 margin 是 50px，因为较小的顶部 margin 与较大的底部 margin 相结合。第二个元素与第三个元素之间的 margin 是 3em，因为 3em 大于第二个元素底部 margin 20px。

### html

```html
<div class="wrapper">
  <div class="box example1">
    margin-top: 50px; margin-bottom: 50px;
  </div>
  <div class="box example2">
    margin-top: 20px; margin-bottom: 20px;
  </div>
  <div class="box example3">
    margin-top: 3em; margin-bottom: 3em;
  </div>
</div>
```

### css

```css
.wrapper {
  border: 5px dotted black;
}
.example1 {
  margin: 50px 0 50px 0;
}
.example2 {
  margin: 20px 0 20px 0;
}
.example3 {
  margin: 3em 0 3em 0;
}
.box {
  background-color: rgb(55, 55, 110);
  color: white;
  padding: 20px;
  border-radius: 0.5em;
}
```

### 运行结果

{% raw %}

  <style>
.day2-wrapper {
  border: 5px dotted black;
}
.example1 {
margin: 50px 0 50px 0;
}
.example2 {
margin: 20px 0 20px 0;
}
.example3 {
margin: 3em 0 3em 0;
}
.day2-box {
background-color: rgb(55, 55, 110);
color: white;
padding: 20px;
border-radius: 0.5em;
}
</style>
<div class="day2-wrapper">
  <div class="day2-box example1">
    margin-top: 50px; margin-bottom: 50px;
  </div>
  <div class="day2-box example2">
    margin-top: 20px; margin-bottom: 20px;
  </div>
  <div class="day2-box example3">
    margin-top: 3em; margin-bottom: 3em;
  </div>
</div>
{% endraw %}

# 完全空盒子

如果一个盒子是空的，那么它的顶部和底部 margin 可能会相互重叠。在下面的示例中，class 为 empty 的元素的顶部和底部 margin 各为 50px，但是，第一项和第三项之间的 margin 不是 100px，而是 50px。这是由于两个 margin 重叠造成的。如果向空盒子中放入内容就会阻止 margin 合并。

### html

```html
<div class="wrapper">
  <div class="box">
    A box
  </div>
  <div class="box empty"></div>
  <div class="box">
    Another box
  </div>
</div>
```

### css

```css
.wrapper {
  border: 5px dotted black;
}
.box {
  background-color: rgb(55, 55, 110);
  color: white;
  border-radius: 0.5em;
}
.empty {
  margin: 50px 0 50px 0;
}
```

### 运行效果

{% raw %}

<div class="day2-wrapper2">

<div class="bay2-box2">
  A box
</div>

<div class="bay2-box2 empty"></div>

<div class="bay2-box2">
  Another box
</div>
  
</div>

<style>
.day2-wrapper2 {
  border: 5px dotted black;
}


.bay2-box2 {
  background-color: rgb(55,55,110);
  color: white;
  border-radius: .5em;
}

.empty {
  margin: 50px 0 50px 0;
}
</style>

{% endraw %}

# 父元素和第一个或最后一个子元素

margin 重叠让人猝不及防，因为它有时候不是很直观。在下面的示例中，有一个类名为 wrapper 的 div，给这个 div 一个红色的 outline，这样就可以看到它在哪里了。

这个 div 里面的三个子元素的 margin 都是 50px。但是你会发现实际的效果是第一项和最后一项与父元素的的 margin 齐平，好像子元素和父元素之间没有 50px 的 margin 一样。

### html

```html
<div class="wrapper">
  <div class="box">
    Item 1
  </div>
  <div class="box">
    Item 2
  </div>
  <div class="box">
    Item 3
  </div>
</div>
```

### css

```css
.wrapper {
  outline: 1px solid #bebeb9;
}

.box {
  margin: 50px;
}

.box {
  background-color: rgb(55, 55, 110);
  color: white;
  padding: 20px;
  border-radius: 0.5em;
}
```

### 运行效果

{% raw %}

<div class="day2-wrapper3">
  <div class="day2-box3">
    Item 1
  </div>
  <div class="day2-box3">
    Item 2
  </div>
  <div class="day2-box3">
    Item 3
  </div>
</div>
<style>
.day2-wrapper3 {
  outline: 1px solid #bebeb9;
}

.day2-box3 {
margin: 50px;
}
.day2-box3 {
background-color: rgb(55,55,110);
color: white;
padding: 20px;
border-radius: .5em;
}
</style>
{% endraw %}

这是因为子节点上的 margin 会随着父节点上的任何一边的 margin 相互重叠，从而最终位于父节点的外部。如果使用 DevTools 检查第一个子元素，就可以看到这一点，显示的黄色区域就是是 margin。

![](https://user-gold-cdn.xitu.io/2019/7/31/16c455d87d0cd57a?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

# 仅块元素 margin 重叠

### html

```html
<div class="wrap">
  <span class="day2-box4">Item 1</span>
  <span class="day2-box4">Item 2</span>
</div>
```

### css

```css
.wrap {
  outline: 1px solid #bebeb9;
}
.day2-box4 {
  width: 86%;
  display: inline-block;
  background-color: rgb(55, 55, 110);
  color: white;
  padding: 20px;
  border-radius: 0.5em;
  margin: 20px;
}
```

### 运行效果

{% raw %}

  <div class="wrap">
    <span class="day2-box4">Item 1</span>
    <span class="day2-box4">Item 2</span>
  </div>
  <style>
    .wrap{
      outline: 1px solid #bebeb9;
    }
    .day2-box4{
      width: 86%;
      display: inline-block;
      background-color: rgb(55,55,110);
      color: white;
      padding: 20px;
      border-radius: .5em;
      margin: 20px;
    }
  </style>
{% endraw %}

# 阻止 margin 重叠

### 常规

- 绝对的定位
- 浮动
- flex
- grid

### 完全为空的盒子

- 如果它有 border 或 padding，它的上下 margin 就不会重叠。

我们将上面的空盒子的代码扒下来 加个 border 属性看看执行结果

### html

```html
<div class="wrapper">
  <div class="box">
    A box
  </div>
  <div class="box empty empty1"></div>
  <div class="box">
    Another box
  </div>
</div>
```

### css

```css
.wrapper {
  border: 5px dotted black;
}
.box {
  background-color: rgb(55, 55, 110);
  color: white;
  border-radius: 0.5em;
}
.empty {
  margin: 50px 0 50px 0;
}
.empty1 {
  border: 1px solid rgb(55, 55, 110);
}
```

### 运行效果

{% raw %}

<div class="day2-wrapper2">

<div class="bay2-box2">
  A box
</div>

<div class="bay2-box2 empty empty1"></div>

<div class="bay2-box2">
  Another box
</div>
  
</div>

<style>
.day2-wrapper2 {
  border: 5px dotted black;
}


.bay2-box2 {
  background-color: rgb(55,55,110);
  color: white;
  border-radius: .5em;
}

.empty {
  margin: 50px 0 50px 0;
}

.empty1 {
  border: 1px solid rgb(55,55,110);
}
</style>

{% endraw %}

#### 添加了 border 后我们发现 margin 生效了

这背后是有逻辑，如果盒子是完全空的，没有 border 或 padding，它基本上是不可见的。 它可能是 CMS 中标记为空的段落元素。 如果你的 CMS 添加了多余的段落元素，你可能不希望它们在其他段落之间造成较大的空白，这时 margin 重叠就有一定的意义。

### 父元素和第一个或最后一个子元素

- 如果我们向父级添加 border，则子级上的 margin 会保留在内部。

我们将上面的父元素和第一个或最后一个子元素的代码扒下来 加个 border 属性看看执行结果

### html

```html
<div class="wrapper wrapper-1">
  <div class="box">
    Item 1
  </div>
  <div class="box">
    Item 2
  </div>
  <div class="box">
    Item 3
  </div>
</div>
```

### css

```css
.wrapper {
  outline: 1px solid #bebeb9;
}
.wrapper-1 {
  border: 5px dotted #bebeb9;
}
.box {
  background-color: rgb(55, 55, 110);
  color: white;
  padding: 20px;
  border-radius: 0.5em;
  margin: 50px;
}
```

### 运行效果

{% raw %}

<div class="day2-wrapper3 day2-wrapper3-1">
  <div class="day2-box3">
    Item 1
  </div>
  <div class="day2-box3">
    Item 2
  </div>
  <div class="day2-box3">
    Item 3
  </div>
</div>
<style>
.day2-wrapper3 {
  outline: 1px solid #bebeb9;
}
.day2-wrapper3-1 {
  border: 5px dotted #bebeb9 ;
}

.day2-box3 {
margin: 50px;
}
.day2-box3 {
background-color: rgb(55,55,110);
color: white;
padding: 20px;
border-radius: .5em;
}
</style>
{% endraw %}

#### 添加了 border 后我们发现 margin 再次生效了

同样，这种行为也有一定的逻辑。如果出于语义目的而对元素进行包装，但这些元素不显示在屏幕上，那么你可能不希望它们在显示中引入大的 margin。当 web 主要是文本时，这很有意义。当我们使用元素来布局设计时，它的重叠行为就没有多大的意义了。

# BFC（Block Formatting Context）格式化上下文

<b>BFC（Block Formatting Context）格式化上下文</b>，是 Web 页面中盒模型布局的 CSS 渲染模式，指一个独立的渲染区域或者说是一个隔离的独立容器。

BFC 可以阻止边距的重叠。 如果我们再看父元素和第一个或最后一个子元素的示例，可以在 wrapper 元素加上 display: flow-root 就会创建一个新的 BFC，从而阻止 margin 合并

### html

```html
<div class="wrapper wrapper-2">
  <div class="box">
    Item 1
  </div>
  <div class="box">
    Item 2
  </div>
  <div class="box">
    Item 3
  </div>
</div>
```

### css

```css
.wrapper {
  outline: 1px solid #bebeb9;
}
.wrapper-2 {
  display: flow-root;
}
.box {
  background-color: rgb(55, 55, 110);
  color: white;
  padding: 20px;
  border-radius: 0.5em;
  margin: 50px;
}
```

### 运行效果

{% raw %}

<div class="day2-wrapper3 day2-wrapper3-2">
  <div class="day2-box3">
    Item 1
  </div>
  <div class="day2-box3">
    Item 2
  </div>
  <div class="day2-box3">
    Item 3
  </div>
</div>
<style>
.day2-wrapper3 {
  outline: 1px solid #bebeb9;
}
.day2-wrapper3-2 {
  display: flow-root;
}

.day2-box3 {
margin: 50px;
}
.day2-box3 {
background-color: rgb(55,55,110);
color: white;
padding: 20px;
border-radius: .5em;
}
</style>
{% endraw %}
