---
title: LIS：最长上升子序列问题及其应用
date: 2021-03-04 00:00:00
categories:
 - 数据结构与算法
tags:
 - DP
 - Greedy Algorithm
 - Binary Search
---

## 算法一：动态规划

容易想到$O(n^2)$的DP：

令$dp_i$表示包含$x_i$元素的，前$i$个元素的，最长上升子序列的长度，
状态转移方程为$dp_i=max(dp_j)+1, 0\le j< i, x_j< x_i$
，答案即为dp数组中最大的元素。

## 算法二：贪心+二分查找

[官方题解](https://leetcode-cn.com/problems/longest-increasing-subsequence/solution/zui-chang-shang-sheng-zi-xu-lie-by-leetcode-soluti/)
可以做到$O(n\log n)$，但实在是太难想出来了。

## 应用：

- [俄罗斯套娃信封问题](https://leetcode-cn.com/problems/russian-doll-envelopes/)
- [堆箱子](https://leetcode-cn.com/problems/pile-box-lcci/)

