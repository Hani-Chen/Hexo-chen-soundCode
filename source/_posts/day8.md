---
title: js - 预加载
abbrlink: 44140
date: 2019-08-28 09:00:19
tags: web前端
categories: web前端 - js组件
---

# js - 预加载

## 预加载 js 封装函数

```JavaScript
// 预加载函数
/**
 *  预加载图片资源
 * @param {Array} names 图片名数组
 * @param {Function} cb 加载回调
 * @param {String} prefix 图片路径配置
 */
function preloadImage(names, cb, prefix, onProgress) {
  var n = 0,
    img,
    imgs = {}
  names.forEach(function(name) {
    img = new Image()
    img.onload = (function(name, img) {
      return function() {
        imgs[name] = img
        n++
        onProgress(n, names.length)
        n === names.length && cb && cb(imgs)
      }
    })(name, img)
    img.src = (prefix || '') + name
  })
}
```

## 预加载 js 封装函数 - 使用

```JavaScript

// 当浏览器准备好了
$(document).ready(function() {
  // 需要加载的静态资源的数组
  var imgs = [
    'text1.png',
    'text2.png'
  ]

  preloadImage('图片数组','当加载完成时回调','当前数组图片的路径','加载时回调 n - 当前加载到第几张，total - 当前加载的静态资源总数')
  preloadImage(imgs,function() {},'./img/',function(n, total){})
})
```
