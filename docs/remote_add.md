---
title: 为 git 同时添加两个远程仓库
date: 2020-10-16 17:36:00
categories:
 - Git
tags:
 - git
 - git remote

---

:::details
参考链接：

一份代码怎么在两处地方做代码管理？ - 燕南的回答 - 知乎 https://www.zhihu.com/question/28563469/answer/41284272
:::



GitHub Pages 最近在境内访问不了了，所以把页面托管到了Gitee上，虽然Gitee Pages每次上传都要手动更新，但是上传和访问速度也快了不少。

写博客，不想局限在一台终端上，于是想用git来管理这个vuepress项目，最方便的办法是在gitee的blog库上新建一个source分支用来管理，我也是这么做的。

但是又想在GitHub上面也放一份作为备份，为git同时添加两个远程仓库就很有必要了。

## 多地址的 remote repo

```bash
git remote set-url origin --add https://github.com/USERNAME/REPO1.git
git remote set-url origin --add https://github.com/USERNAME/REPO2.git
```

在 .git/config 里可以看到

```
...
[remote "origin"]
    url = https://USERNAME@github.com/USERNAME/REPO1.git
    url = https://USERNAME@github.com/USERNAME/REPO2.git
...
[branch "master"] 
    remote = origin
...
```

然后

```bash
git push origin master
```

就会同时提交到两个 repo，而

```bash
git pull origin master
```

会从两个 repo 里取得更新。

当然 URL 和 repo 不一定非要是 GitHub 上的，具有两个 url 的 remote 也不一定要是 origin，比如可以设置成 all。

## 只用于push的备份repo

你想从 repo1 pull，但是 push 的时候要推送到 repo1 和另一个 repo2，

```bash
git remote set-url origin --add https://github.com/USERNAME/REPO1.git
git remote set-url origin --push --add https://github.com/USERNAME/REPO1.git
git remote set-url origin --push --add https://example.com/USERNAME/REPO2.git
```

在 .git/config 里可以看到

```
...
[remote "origin"]
    url = https://USERNAME@github.com/USERNAME/REPO1.git
    pushurl = https://USERNAME@github.com/USERNAME/REPO1.git
    pushurl = https://USERNAME@example.com/USERNAME/REPO2.git
...
[branch "master"] 
    remote = origin
...
```

然后

```
git push origin master
```

就会同时提交到两个 repo，而

```
git pull origin master
```

会从两个 GitHub repo1 里取得更新。