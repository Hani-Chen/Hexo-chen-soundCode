---
title: html - 弹窗组件
abbrlink: 27821
date: 2019-09-27 20:51:42
tags: [web前端, web前端 - html]
categories: [web前端 - 实用组件, 弹窗组件]
---

# html - 弹窗组件

## 简单明了直接码代码！！！

### HTML 代码块

```html
<!-- 弹窗 -->
<div class="modal show" id="gloryModal">
  <div class="modal-content">
    <!-- 背景 -->
    <div class="modal-bg"></div>
    <div class="modal-body">
      <!-- 关闭按钮 -->
      <span class="modal-close"></span>
      <!-- 弹窗内容区 -->
    </div>
  </div>
</div>
<span id="btn">点击显示弹窗</span>
```

### scss 代码块 

```css
// 阻止全屏后页面滚动
html,
body {
  height: 100%;
}
body.overflow {
  overflow: hidden;
  height: 100%;
}
/* 弹窗 - 定位容器 */
.modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
  z-index: 1000;
  
}
.modal.show {
    display: block;
  }
  /* 弹窗 - 内容容器 */
  .modal-content {
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  /* 弹窗 - 背景容器 */
  .modal-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.9);
    z-index: 1;
  }
  /* 弹窗 - 内容 */
  .modal-body {
    position: relative;
    max-width: 100%;
    margin: 0 auto;
    z-index: 2;
  }
  /* 弹窗 - 关闭 */
  .modal-close {
    position: fixed;
    right: 60px;
    top: 60px;
    width: 50px;
    height: 50px;
    text-align: center;
    line-height: 50px;
    background: #f00;
    background-image: url(../img/modal-close.png);
    background-size: 40px 40px;
    background-position: center;
    background-repeat: no-repat;
    cursor: pointer;
  }
#btn{
  display: block;
  width: 150px;
  height: 36px;
  border: 1px solid #999;
  border-radius: 6px;
  text-align: center;
  line-height: 36px;
  margin-top: 20px;
  cursor: pointer;
}
```

```JavaScript
  /**
   * 按ID显示弹窗
   */
  function showModal(id) {
    $('#' + id).addClass('show')
  }

  /**
   * 按ID隐藏弹窗
   */
  function hideModal(id) {
    $('#' + id).removeClass('show')
  }

  // 弹窗关闭按钮事件
  $('body').on('click', '.modal-close', function() {
    $(this).parents('.modal').removeClass('show')
    $('body').removeClass('overflow')
  })

  // 弹窗关闭按钮事件
  $('#btn').on('click', function() {
    // 显示弹窗
    showModal('gloryModal')
    // 静止滚动
    $('body').addClass('overflow')
  })

```

### 代码运行结果
{% raw %}
<style>
html,
body {
  height: 100%;
}
body.overflow {
  overflow: hidden;
  height: 100%;
}
/* 弹窗 - 定位容器 */
.modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
  z-index: 1000;
  
}
.modal.show {
    display: block;
  }
  /* 弹窗 - 内容容器 */
  .modal-content {
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  /* 弹窗 - 背景容器 */
  .modal-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.9);
    z-index: 1;
  }
  /* 弹窗 - 内容 */
  .modal-body {
    position: relative;
    max-width: 100%;
    margin: 0 auto;
    z-index: 2;
  }
  /* 弹窗 - 关闭 */
  .modal-close {
    position: fixed;
    right: 60px;
    top: 60px;
    width: 50px;
    height: 50px;
    text-align: center;
    line-height: 50px;
    background: #f00;
    background-image: url(../img/modal-close.png);
    background-size: 40px 40px;
    background-position: center;
    background-repeat: no-repat;
    cursor: pointer;
  }
#btn{
  display: block;
  width: 150px;
  height: 36px;
  margin-top: 20px;
  border: 1px solid #999;
  border-radius: 6px;
  text-align: center;
  line-height: 36px;
  cursor: pointer;
}
</style>
<!-- 弹窗 -->
<div class="modal" id="gloryModal">
  <div class="modal-content">
    <!-- 背景 -->
    <div class="modal-bg"></div>
    <div class="modal-body">
      <!-- 关闭按钮 -->
      <span class="modal-close">X</span>
      <!-- 弹窗内容区 -->
      <p>我是弹窗内容</p>
    </div>
  </div>
</div>
<span id="btn">点击显示弹窗</span>
<script>
/**
 * 按ID显示弹窗
*/
function showModal(id) {
  $('#' + id).addClass('show')
}

/**
 * 按ID隐藏弹窗
*/
function hideModal(id) {
  $('#' + id).removeClass('show')
}

// 弹窗关闭按钮事件
$('body').on('click', '.modal-close', function() {
  $(this).parents('.modal').removeClass('show')
  $('body').removeClass('overflow')
})

// 弹窗关闭按钮事件
$('#btn').on('click', function() {
  // 显示弹窗
  showModal('gloryModal')
  // 静止滚动
  $('body').addClass('overflow')
})
</script>
{% endraw %}
