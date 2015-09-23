---
layout: post
title: "git 本地修改及文件上传"
date: 2015-07-12
---

初次使用时，先创建一个新的文件夹以将要的仓库名上传。然后在bash命令下cd 打开新建的文件夹. 

**ps:你的github账户要有同名文件夹。**

```git init```

初始化 #.git#文件夹

```
git add .
git commit -m "what's up"
```


将当前的改动提交到本地仓库，并写入本次提交的注释是”what's up“

```
git remote add origin https://github.com/username/projectname.git
git push origin 
```

以https方式push后会提示输入用户名和密码。

```
git remote add origin git@github.com:username/projectname.git
git push origin
```

以shh方式避免输入用户名和密码。

*ps: 提前设定好shh*

~poi~poi~poi~poi~poi~poi~poi~poi~poi~poi~poi~poi~poi~poi~

以后的每次修改

```
git add .
git commit -m "penta kill"
git push -u origin 
```