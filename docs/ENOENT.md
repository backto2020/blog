---
title: 【转载】Why does ENOENT mean “No such file or directory”?
date: 2021-02-05 00:00:00
categories:
 - 未分类
tags:
 - bash
---

[What does the `ENT` mean in `ENOENT`?](https://stackoverflow.com/questions/19902828/why-does-enoent-mean-no-such-file-or-directory)

Shouldn't the error:

> No such file or directory

just be named by ENOFILE?

Is there any story or reason?

---

Answers:

It's an abbreviation of Error NO ENTry (or Error NO ENTity), and can actually be used for more than files/directories.

It's abbreviated because C compilers at the dawn of time didn't support more than 8 characters in symbols.

