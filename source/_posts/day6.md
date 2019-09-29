---
title: 博客搭建 hexo框架搭建
abbrlink: 63785
date: 2019-08-08 09:00:00
tags: [web前端, web前端 - 环境配置]
categories: [web前端 - 框架搭建, web前端 - 环境配置]
---

# Hexo 博客搭建图文教程

## **Node.js** 环境配置 

我们可以去 [**官网**](https://nodejs.org/en/) 直接下载相对应的 node 版本

或者直接点击下载

- [**Windows Installer 32-bit**](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x86.msi)
- [**Windows Installer 64-bit**](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x64.msi)

根据自己的 Windows 版本选择相应的安装文件 现在的机子基本都是 64 位的，不知道的选择 64 位的安装包

**保持默认设置即可，一路 Next，安装很快就结束了。**

### 安装好后我们看一下 **Node.js** 环境是否配置成功

- 首先使用快捷键 `Win + R` 运行窗口
- - 在新打开的窗口中输入 cmd，敲击回车，打开命令行界面。

- 或者返回桌面使用方式 `shift + 鼠标右键` 选择在此处打开命令窗口

在打开的命令行界面中，输入

```JavaScript
node -v
npm -v
```

**如果结果如下图所示，则说明安装正确，可以进行下一步了，如果不正确，则需要回头检查自己的安装过程。** <br/>
![](/images/day6/test.png)

## **Git** 环境配置 

同样你也可以去 [**官网**](https://git-scm.com/) 直接下载相对应的 Git 版本

或者直接点击下载

- [**用于 Windows 安装程序的 32 位 Git**](https://github.com/git-for-windows/git/releases/download/v2.22.0.windows.1/Git-2.22.0-32-bit.exe)
- [**用于 Windows 安装程序的 64 位 Git**](https://github.com/git-for-windows/git/releases/download/v2.22.0.windows.1/Git-2.22.0-64-bit.exe)

也是根据自己的 Windows 版本选择相应的安装文件 现在的机子基本都是 64 位的，不知道的选择 64 位的安装包

同样在打开的命令行界面中，输入

```JavaScript
git --version
```

**同样如果结果如下图所示，则说明安装正确，可以进行下一步了，如果不正确，则需要回头检查自己的安装过程。** <br/>
![](/images/day6/test1.png)

## 配置 gitHub (注册账号)

- **如果已经拥有账号，请跳过此步~**

- 点击 [注册](https://github.com/) 分别填入自己的用户名，邮箱，密码。填写完成之后去邮箱查看注册填写的邮件 查看收件箱
- 点开 gitHub 发送给你的注册确认信，确认注册，结束注册流程。
  **一定要确认注册，否则无法使用！**

## 创建 gitHub 仓库

注册完成后登陆 gitHub 点击左上角 `New` 创建项目

- 进入代码库创建页面：
  ![](/images/day6/test2.png)
  Repository name 下填写 yourname.github.io
  Description (optional) 下填写仓库描述 (可为空)
  填完之后直接点创建就好
  创建完成后是这样的
  ![](/images/day6/test5.png)

## 密钥生成 添加

我们回到桌面 右键 点击 `Git Bash Here` 进入 (如果么有这个选项请回到 Git 环境配置)
进入后分别输入

```javasript
cd ~/.ssh
ls
```

## 配置 Hexo

首先我们在电脑上的任意位置创建一个文件夹(就是你以后的博客项目了)

同样 `shift + 鼠标右键` 选择在此处打开命令窗口。

在命令行中输入：

```javasript
npm install hexo-cli -g
```

执行完之后 接着在命令行中输入：

```javasript
npm install hexo --save
```

然后你会看到命令行窗口刷了一大堆白字，执行完成之后我们来看一看 Hexo 是不是已经安装好了。 在命令行中输入：

```javasript
hexo -v
```

**如果结果如下图所示，则说明安装正确，可以进行下一步了，如果不正确，则需要回头检查自己的安装过程。** <br/>
![](/images/day6/test3.png)

紧接着我们要初始化 hexo

我们继续在命令行中输入：

```javasript
hexo init
```

**如果执行结果如下图所示，则说明初始化成功，可以进行下一步了，如果不正确，则需要回头检查自己的初始化过程。** <br/>
![](/images/day6/test4.png)

之后我们要安装依赖我们继续在命令行中输入：

```javasript
npm install
```

之后 npm 将会自动安装你需要的组件，只需要等待 npm 操作即可。

## 首次体验 Hexo

同样是在命令行中，输入：

```javasript
hexo g
```

等操作完成之后继续输入：

```javasript
hexo s
```

执行完成之后就会提示

```javasript
Hexo is running at http://localhost:4000 . Press Ctrl+C to stop
```

在浏览器中打开 http://localhost:4000/ 你将会看到一个完美的博客就展示在我们面前了

关于 hexo 的配置我们可以去 [官网](https://hexo.io/zh-cn/) 瞅瞅

## 关联 gitHub 仓库

打开 `Hexo` 项目文件夹 找到配置文件\_config.yml，翻到最后：

```javasript
deploy:
type:
```

将他修改成：

```javasript
deploy:
type: git
repo: 这里填入你之前在GitHub上创建仓库的完整链接（在创建仓库时提到的那个地址 直接复制过来）
branch: master
```

地址在 创建仓库时提到的那个地址 直接复制过来
