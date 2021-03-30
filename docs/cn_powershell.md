---
title: 修改powershell编码格式
date: 2021-03-14 00:00:00
categories:
 - 未分类
tags:
 - powershell
 - 编码
---

vscode运行代码的时候终端窗口输出的中文乱码，代码的编码是UTF-8，powershell的编码是GB2312。

参考：https://blog.csdn.net/x356982611/article/details/80285930

临时修改只需要用chcp命令：

```
chcp 65001
```

永久修改则需要修改注册表：[HKEY_CURRENT_USER\Console\CodePage]

将CodePage的值从936改为65001。

