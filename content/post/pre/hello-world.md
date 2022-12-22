---
title: "建站一些命令！"
description: "快速的描述下有关于 Hugo 建站的基本用法。"

lastmod: 2000-06-03T16:43:23+08:00
date: 2000-06-02T11:52:03+08:00

categories:
 - hugo说明
tags:
 - Hugo
 - 开始

url: post/pre/hello-world.html

---

> “使用 `weight` 关键字置顶文章。”

[Hugo](https://gohugo.io/) 是现今世界上最快的网站建设框架，也是最流行的开源静态站点生成器之一。 凭借其惊人的速度和灵活性，Hugo 让建设网站再次变得有趣起来。

<!--more-->

## 快速开始

### 发表新文章

```shell
$ hugo server --buildDrafts
```

更多信息：[内容格式](https://gohugo.io/content-management/formats/)

### 创建文件
```shell
hugo new post/first.md
```

### 启动服务以实时预览的方式

```shell
$ hugo server
```

### 启动服务

```shell
$ hugo server
```

更多信息：[Hugo 服务命令行](https://gohugo.io/commands/hugo_server/)

### 生成静态文件
- 为了部署到线上，需要将 Markdown 文件打包成 HTML 文件。打包命令如下，hugo-theme-next 是主题名：(命令必须在网站的根目录下执行)

```shell
$ hugo -t hugo-theme-next
```
```shell
$  hugo --theme=hyde hugo-theme-next
```


更多信息：[Hugo 建站](https://gohugo.io/commands/hugo/)

### 部署到服务器

```language
$ hugo deploy
```

更多信息：[Hugo 发布](https://gohugo.io/commands/hugo_deploy/)

祝你好运，相信你会喜欢上 Hugo 建站的旅程！