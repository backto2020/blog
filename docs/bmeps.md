---
title: 使用bmeps命令将图片转EPS格式
date: 2020-11-10 00:00:00
categories:
 - 未分类
tags:
 - latex
 - eps
---

latex编译文章时，图片格式只能使用 .eps 格式。

一开始在网上在线转换，后来发现 texlive 自带了 bmeps 命令可以方便地将图片转换为 .eps 格式。

```shell
bmeps -c picturename.png picturename.eps
```

![bmeps](pic/bmeps.png)

```shell
where bmeps
```

![where_bmeps](pic/wherebmeps.png)