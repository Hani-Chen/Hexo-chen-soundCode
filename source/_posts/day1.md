---
title: case1
tags: web前端开发-案例实现
categories: web前端开发
abbrlink: 43968
date: 2019-07-30 13:14:52
---

{% raw %}

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    .day1-btn {display: block;width: 160px;height: 36px;background: #666;text-align: center;line-height: 36px;color: #fff;order-radius: 4px;margin: 20px auto;cursor: pointer;user-select: none;} /* 按钮样式 */
    .day4-box {width: 100%;height: 200px;background: rgb(150, 116, 179);transition: height 0.6s;} /* 案例四样式 */
    .day4-box-hide {height: 0;}
  </style>
</head>
<body>
  <div>
    <div class="day4-box"></div>
    <span class="day1-btn" id="case4-btn">点击显示隐藏</span>
  </div>
  <script>
    function $(id) {
      if (id.substr(0, 1) == '.') {
        id = id.substring(1)
        return document.getElementsByClassName(id)
      } else if (id.substr(0, 1) == '#') {
        id = id.substring(1)
        return document.getElementById(id)
      }
    }
    // 案例四
    // 点击隐藏
    $('#case4-btn').onclick = function () {
      // 点击 .day4-box 判断是否拥有 day4-box-hide 这个类名
      if ($('.day4-box')[0].classList.contains('day4-box-hide')) {
        // 如果有就移除
        $('.day4-box')[0].classList.remove('day4-box-hide')
      } else {
        // 如果没有就添加
        $('.day4-box')[0].classList.add('day4-box-hide')
      }
    }
  </script>
</body>
</html>
{% endraw %}