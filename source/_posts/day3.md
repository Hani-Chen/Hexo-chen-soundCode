---
title: AE 导出json动画文件 开发渲染动画
tags: web前端开发-文章介绍
categories: web前端开发
abbrlink: 44359
date: 2019-08-01 21:30:30
---

首先我们需要动画师输出给我们一个 JSON 动画文件

然后我们的主角 `lottie.js` 要出场了

我们通过 `npm i lottie-web -s` 下载 **lottie.js**

下载完成后 我们就开始使用吧

html 代码块

```html
<!-- 包含动画的dom元素 -->
<div id="animation"></div>
<!-- 引入lottie.js -->
<script src="./js/lottie.js"></script>
```

css 代码块

```css
* {
  margin: 0;
  padding: 0;
}
html,
body {
  width: 100%;
  height: 100%;
}
#animation {
  width: 100%;
  height: 100%;
  background: #666;
}
```

js 代码块

```javascript
var icon = document.getElementById('animation')
lottie.loadAnimation({
  container: icon, // 包含动画的dom元素
  renderer: 'html', //渲染方式，有"html"、"canvas"和"svg"三种
  loop: true, //循环播放
  autoplay: true, //自动播放
  path: '../json/03.json' // 动画json的路径
})
```

这就是最简单的渲染 json 动画

运行结果
{% raw %}

<style>

#animation {
  position:relative;
  width: 100%;
  padding-bottom:50%;
  background: #666;
}
</style>

<div id="animation"></div>
<!-- 引入lottie.js -->
<script src="/js/lottie.js"></script>
<script>
var  icon = document.getElementById('animation')
lottie.loadAnimation({
    container: icon, // 包含动画的dom元素
    renderer: 'html', //渲染方式，有"html"、"canvas"和"svg"三种
    loop: true,  //循环播放
    autoplay: true, //自动播放
    path: '/js/03.json' // 动画json的路径
});
</script>

{% endraw %}
