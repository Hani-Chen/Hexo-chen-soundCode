---
title: 音频插件 howler 使用
tags: web前端
categories: [web前端 - 插件学习, web前端 - 案例实现]
abbrlink: 46904
date: 2019-08-06 21:30:30
---

# **点击按钮播放背景音效**

用插件之前我们是要引入插件库的 本篇文章使用 `howler.js` 本地引入
一个 JSON 动画文件

然后我们的主角 `howler.js` 要出场了

我们通过 `cnpm i howler -s` 下载 **howler.js**

废话不多说咱直接上代码

###  html 代码块

```html
<!-- 我们就只用两个按钮来做本次demo演示 -->
<button class="play">播放</button>
<button class="stop">暂停</button>

<!-- 引入howler -->
<script src="/js/howler.min.js" type='text/javascripnt'></script>

```

### js 代码块

```js
// 查看按钮音效
// 创建实例
var viewSound = new Howl({
  /* 音频路径 可用相对路径 */
  src: ['/audio/alert.mp3'],
  /* 是否循环播放 默认为 false */
  autoplay: false,
  /* 是否循环播放 默认为 false */
  loop: false,
  /* 设置声音大小，从 0.0 到 1.0 */
  volume: 1,

  onend: function() {
    console.log('自动结束!')
  },
  onstop: function() {
    console.log('暂停!')
  },
  onplay: function() {
    console.log('播放!')
  }
})

var stop = document.getElementsByClassName('stop')[0]
var play = document.getElementsByClassName('play')[0]
stop.onclick = function() {
  /* 暂停音效 */
  viewSound.stop()
}
play.onclick = function() {
  /* 播放音效 */
  viewSound.play()
}
```

### 操作实例

{% raw %}

<!-- 我们就只用两个按钮来做本次demo演示 -->

<button class="play">播放</button>
<button class="stop">暂停</button>

<!-- 引入howler -->
<script src="/js/howler.min.js" type='text/javascripnt'></script>
<script>
var viewSound = new Howl({
  /* 音频路径 */
  src: ['/audio/alert.mp3'],
  /* 是否循环播放 默认为 false */
  autoplay: false,
  /* 是否循环播放 默认为 false */
  loop: false,
  /* 设置声音大小，从 0.0 到 1.0 */
  volume: 1,

  onend: function() {
    console.log('自动结束!')
  },
  onstop: function() {
    console.log('暂停!')
  },
  onplay: function() {
    console.log('播放!')
  }
})
var stop = document.getElementsByClassName('stop')[0]
var play = document.getElementsByClassName('play')[0]
stop.onclick = function() {
  /* 暂停音效 */
  viewSound.stop()
}
play.onclick = function() {
  /* 播放音效 */
  viewSound.play() 
}
</script>

{% endraw %}
