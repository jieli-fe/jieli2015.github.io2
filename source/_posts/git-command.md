---
title: git常用命令
date: 2017-07-25 14:55:19
tags: git
---
好久不用git，有些命令都生疏了。 罗列一些，加强记忆
<!-- more -->
常用操作
```js
//初始化git目录
git init 

// 克隆远端的仓库(新建一个仓库名称的文件夹)
git clone username@host:/path/to/repository

//推送到远端 master 分支
git push origin master

// 关联远端仓库
git remote add origin 仓库地址

//删除关联的远端擦那干枯
git remote rm origin

// 增加暂存区文件
git add . //所有文件
git add -u //新增加文件除外


// 查看状态
git status

// 撤销暂存区所有的修改.
// 慎用，会覆盖本地所有修改，白干一天。。。
git checkout .

```

特殊操作
```js
// 配置别名
git config --global alias.st status
git st 
// 等于如下命令
git status

// 关联dev分支
git branch --set-upstream dev origin/dev

```


