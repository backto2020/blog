---
title: 快速判断错误的出栈顺序
date: 2020-11-5 00:00:00
categories:
 - 数据结构与算法
tags:
 - stack
---

假设给定一个入栈序列$a_1, a_2, a_3, a_4, ..., a_n$，如何快速判断错误的出栈序列？

**规律：出栈序列的每一个元素后面，比该元素先入栈的，一定按照入栈顺序的逆序排列。**

