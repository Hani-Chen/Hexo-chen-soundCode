---
title: 动画插件 lottie 使用
tags: web前端
categories: web前端 - 插件学习
abbrlink: 44360
date: 2019-08-01 21:30:30
---

# **AE 导出 json 动画文件 开发渲染动画**

首先我们需要动画师输出给我们一个 JSON 动画文件

然后我们的主角 `lottie.js` 要出场了

我们通过 `npm i lottie-web -s` 下载 **lottie.js**

下载完成后 我们就开始使用吧

html 代码块

```html
<!-- 包含动画的dom元素 -->
<div id="animation"></div>
<button class="stop">停止</button>
<button class="play">播放</button>
<button class="pause">暂停</button>
<!-- 引入lottie.js -->
<script src="/js/lottie.js" type='text/javascripnt'></script>
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
  path: 'json/01.json' // 动画json的路径
})
var stop = document.getElementsByClassName('stop')[0]
var play = document.getElementsByClassName('play')[0]
var pause = document.getElementsByClassName('pause')[0]
// 停止动画
stop.onclick = function() {
  lottie.stop()
}
// 播放动画
play.onclick = function() {
  lottie.play()
}
// 暂停动画
pause.onclick = function() {
  lottie.pause()
}
```

### 操作实例

{% raw %}

<style>
* {margin: 0;padding: 0;}
html,body {width: 100%;height: 100%;}
#animation {width: 100%;height: 100%;background: #666;}
</style>

<!-- 包含动画的dom元素 -->
<div id="animation"></div>
<button class="stop">停止</button>
<button class="play">播放</button>
<button class="pause">暂停</button>
<!-- 引入lottie.js -->
<script src="/js/lottie.js" type='text/javascripnt'></script>
<script>
var icon = document.getElementById('animation')
lottie.loadAnimation({
  container: icon, // 包含动画的dom元素
  renderer: 'html', //渲染方式，有"html"、"canvas"和"svg"三种
  loop: true, //循环播放
  autoplay: true, //自动播放
  path: '/json/03.json' // 动画json的路径
})
var stop = document.getElementsByClassName('stop')[0]
var play = document.getElementsByClassName('play')[0]
var pause = document.getElementsByClassName('pause')[0]
// 停止动画
stop.onclick = function() {
  lottie.stop()
}
// 播放动画
play.onclick = function() {
  lottie.play()
}
// 暂停动画
pause.onclick = function() {
  lottie.pause()
}
</script>

{% endraw %}

这就是最简单的渲染 json 动画

# 注 ：另外 canvas 渲染不支持 json 动画中包含文字 所以 json 动画文件中如果有文字请谨慎使用
