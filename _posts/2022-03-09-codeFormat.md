---
title: Clang-format结合Xcode File-template、Code Snippet探索iOS代码规范实践
author:
  name: irick
  link: https://github.com/Happyirick
date: 2022-03-09 19:55:00 +0800
categories: [iOS]
tags: [iOS, 代码规范]
pin: false

---

> 代码规范是每一个开发小组在实践中的一个痛点，如何让队伍中尽可能多的人遵循同一套代码风格，产出高质量的代码，同时能够尊重每位开发者的编程习惯，不增加冗余环节，是值得每个工程师思考的问题

在本文中，将利用Clang-format工具结合Xcode自带文件模版、Code Snippet探索iOS代码规范实践

<!-- toc -->

## Clang-format

> ClangFormat describes a set of tools that are built on top of LibFormat. It can support your workflow in a variety of ways including a standalone tool and editor integrations.

Clang-format 是一个代码格式化工具，能够为C/C++/Java/JavaScript/JSON/Objective-C/Protobuf/C#提供格式化规则

### 安装clang-format

\#####通过homebrew下载

```
brew install clang-format
```

\#####查看是否安装成功

```
clang-format --version
```

### 添加clang-format服务

在 **启动台** >> **其他** >> **自动操作** 中选择 **快速操作**

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628663.png)

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628664.png)

##### 脚本代码

```
export PATH=/usr/local/bin:$PATH
clang-format
```

保存服务并命名，例如保存为 **Xcode-clang-format**  （很重要,后面还要用）

### clang-format使用

在当前用户根目录`～` 放入	`.clang-format` 文件

```
touch ~/.clang-format
```

下载链接 [.clang-format](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fhuipengo%2Fclang-format)

具体参数意义详见 [clang-format参数详解](https://www.cnblogs.com/PaulpauL/p/5929753.html)

### 添加clang-format快捷键

**系统设置** >> **键盘** >> **快捷键** >> **APP快捷键** >> **Xcode.app** 添加服务 **Xcode-clang-format** （之前保存的服务名）设置快捷键  **Control** + **I** 

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628666.png)

快去工程里试试吧

**参考资料**

1. [clang-format](https://www.jianshu.com/p/97ac40a78300)
2. [clang-format官方自定义参数介绍](https://www.cnblogs.com/PaulpauL/p/5929753.html)

## Xcode File-template

**Xcode的文件模板路径一般在下面这个目录**

```
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/Xcode/Templates
```

**所有的模板文件即存在File Template/iOS/Source中**

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628673.png)

复制 **source** 文件夹，重命名为 **CustomTemplate** ，即为自定义的文件模板分区

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628671.png)

其中，又分为 **Swift** 和 **OC** 以及带XIB文件的文件夹，其中的 **.h** 和 **.m** 文件即为模板文件

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628670.png)

以 **OC** 的 **ViewController** 为例

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628672.png)

新建 **CustomTemplate** 下的 **ViewController** 文件

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628669.png)

建立好的.m文件

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628668.png)

通过模板，即可实现代码分区和一部分固定方法的重写实现

**参考资料**

1. [Apple宏参数文档](https://help.apple.com/xcode/mac/9.0/index.html?localePath=en.lproj#/dev7fe737ce0)
2. [Xcode模板和Code Snippet](https://www.jianshu.com/p/376f372497b5)

## Code Snippet

新建 **Code Snippet**

![img](https://cdn.jsdelivr.net/gh/HappyiRick/Album/Blogimg/202203171628667.png)

通知、Observer、懒加载、创建单例、贝塞尔曲线等格式化代码，均可通过上述方式存储起来

<!-- endtoc -->
