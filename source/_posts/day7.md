---
title: js - ajax获取接口数据
abbrlink: 43052
date: 2019-08-26 18:10:58
tags: web前端
categories: web前端 - js组件
---
## 简单明了直接码代码！！！

```JavaScript
$.ajax({
  url: 'https://www.easy-mock.com/mock/5d6390b90915be18898ac4bd/Hani-ChenURL/test', //接口链接
  type: 'get', //请求方式
  // 如果获取成功
  success: function(data) {
    //成功时返回的data值
    console.log(data)
    var musicData = data.slider
    console.log(musicData)
  },
  // 如果获取失败
  error: function(err) {
    console.log(err)
  }
})
```