---
title: 尝试添加在博客中添加demo
tags: web前端
categories: web前端 - 案例实现
abbrlink: 43969
date: 2019-07-30 13:14:52
---

{% raw %}

  <style>
    .day1-btn {display: block;width: 160px;height: 36px;background: #666;text-align: center;line-height: 36px;color: #fff;order-radius: 4px;margin: 20px auto;cursor: pointer;user-select: none;} /* 按钮样式 */
    .day4-box {width: 100%;height: 200px;background: rgb(150, 116, 179);transition: height 0.6s;} /* 案例四样式 */
    .day4-box-hide {height: 0;}
  </style>
  <div>
    <div class="day4-box"></div>
    <span class="day1-btn" id="case4-btn">点击显示隐藏</span>
  </div>
  <script>
    // 案例四
    var case4btn = document.getElementById('case4-btn')
    var day4box = document.getElementsByClassName('day4-box')
    // 点击隐藏
    case4btn.onclick = function () {
      // 点击 .day4-box 判断是否拥有 day4-box-hide 这个类名
      if (day4box[0].classList.contains('day4-box-hide')) {
        // 如果有就移除
        day4box[0].classList.remove('day4-box-hide')
      } else {
        // 如果没有就添加
        day4box[0].classList.add('day4-box-hide')
      }
    }
  </script>
{% endraw %}