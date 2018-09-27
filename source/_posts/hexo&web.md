---
title: 对于hexo new的web端构想
date: 2017-02-14 07:55:57
categories: 技术
tags: ["nodejs", "hexo"]
---

用了一段时间的hexo，感觉在pc端用着还是很方便的，但是有一些时候，想用手机在博客上记录一些自己的心情时却无能为力，所以突发奇想想要做一个hexo新建文章的web端，作为一名程序员，想要把一些繁琐的过程自动化实现，最首先的构想就是流程的控制，流程就分为几步：

```
新建文章->修改博文类别等信息->编写markdown内容->更新hexo博客内容->上传到hexo博客仓库
```

以下所有内容都是以nodejs作为后端语言的构想。并且会在本月26号开学之后进行代码的实现

<!--more-->

### 新建文章||新建文章&&修改博文类别信息

用过hexo的都知道，新建文章的命令是hexo new "postname"，那么web端想要进行文章的新建就有两种方法，第一种就是运行hexo命令，第二种就是直接按照hexo new命令新建出来的文件的格式，使用fs进行新建文件，将一些必要信息输入进新建的文件中，个人偏向于使用第二种方法，因为第一种方法的流程控制比较麻烦，需要等hexo new命令，还需要进入新建出的文件进行信息的修改。第二种方法的优势就是可以在web端直接填写一些必要信息，将这些信息收到后直接填入md文件中，之后执行hexo g&d命令。

所以暂时选用第二种方法。

### 编写markdown内容

感觉这部分东西会比较简单，因为有一些很成熟的markdown编辑器，可以看见实时的效果。

这部分内容没有什么好思考的

### 更新hexo博客内容&&上传到仓库

nodejs.process.exec运行hexo g和hexo d命令就可以了

### 安全性问题

在web端新建文章，提交到后端时加上校验就可以了，在json文件中存入一个password，将前端的输入与password进行对比就可以了。不是特别麻烦。