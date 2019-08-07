---
title: day5
abbrlink: 27054
date: 2019-08-07 16:59:19
tags:
---

## vue v-for 后 图片不显示解决方法

``` HTML
<ul class="new-item" v-for="item in lists" :key="item">
   <li class="new-item-img">
      <img :src="item.images" alt>
    </li>
    <li>{{item.text}}</li>
</ul>
```

## 第一种解决方法

- 直接在 lists 中利用 require 语句

```JavaScript
lists: [
  {
    images: require('@/assets/img/index1.jpg'),
    text: '这是文本'
  },
  {
    images: require('@/assets/img/index2.jpg'),
    text: '这是文本'
  },
],
```

## 第二种解决方法

- 先要引入图片

```JavaScript
// 引入图片
import news_img  from "@/assets/img/index1.jpg";
import new_img from "@/assets/img/index2.jpg";
```
- 然后直接用变量的方式写在 lists 中

```JavaScript
lists: [
  {
    images: news_img,
    text: '这是文本'
  },
  {
    images: new_img from,
    text: '这是文本'
  },
],
```

## 第三种方法

- 在项目目录下新建静态文件夹 public 将图片文件放在该目录下的 img 文件夹

![](/images/test.png)

- 之后就可以直接引用图片了 **注意引入时路径不要错了**

``` JavaScript
lists: [
  {
    images:/img/index1.jpg,
    text: '这是文本'
  },
  {
    images: /img/index1.jpg,
    text: '这是文本'
  },
],
```
