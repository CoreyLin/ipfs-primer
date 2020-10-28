# 课程:Pinning - 告诉IPFS保存一个文件

## 目标

本课介绍了在IPFS仓库中“pinning”文件和使用ipfs垃圾收集器删除文件的主题。pinning是IPFS中一个非常重要的概念。pinning是一种机制，允许你告诉IPFS始终将给定对象保持在本地。

学习完这节课，你就能

* 告诉IPFS保留本地IPFS仓库中的特定文件
* 告诉IPFS清除本地IPFS仓库中不需要的文件

## 步骤

### 步骤1:创建要add和pin的文件

创建一个名为`foo.txt`的文件，并将文本“ipfs rocks”放入其中。这里有一个简单的命令行方法来做这个:

```bash
$ echo "ipfs rocks" > foo.txt
```

### 步骤2:将文件添加到IPFS

```bash
$ ipfs add foo.txt
added QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy foo.txt
```

### 步骤3:列出pinned到本地仓库的对象

```bash
$ ipfs pin ls --type=all
QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy recursive
QmY5heUM5qgRubMDD1og9fhCPA6QdkMp3QCwd4s7gJsyE7 indirect
```

上面列出的第一个对象是`foo.txt`文件。默认情况下，通过`ipfs add`添加的对象是递归pinned的。

ipfs世界里有三种pins:

a\) 直接pins，仅仅pin单个block，不pin与之相关的其他blocks;

b\) 递归pins，pin一个给定block及其所有子blocks;

c\) 间接pins，这是递归pin一个给定block的父block的结果。

### 步骤4:unpin一个对象

你可以像这样unpin `foo.txt`:

```bash
$ ipfs pin rm QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
unpinned QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
```

好的，现在验证它不再存在

```bash
$ ipfs cat QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
ipfs rocks
```

等等，它似乎还在那里!好的，你必须运行垃圾收集器，然后再次验证。

```bash
$ ipfs repo gc
removed QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
$ ipfs cat QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
Error: merkledag: not found
```

IPFS有一种相当主动的缓存机制，在对一个对象执行任何IPFS操作后，该机制可以在短时间内将对象保持在本地，但是这些对象可能会相当定期地被垃圾收集。

一个pinned的对象不能被垃圾收集，如果你不相信我试试这个:

```bash
$ ipfs add foo.txt
added QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy foo.txt
$ ipfs repo gc
$ ipfs cat QmRTV3h1jLcACW4FRfdisokkQAk4E4qDhUzGpgdrd4JAFy
ipfs rocks
```

## 解释

IPFS节点将它们存储的数据视为缓存，这意味着不能保证数据将继续存储。pin一个CID(哈希)就是告诉IPFS节点，该数据很重要，不能丢弃。你应该pin你认为重要的内容，以确保内容被长期保留。由于对其他人重要的数据对你可能并不重要，因此pin可以让你控制所需的磁盘空间和数据保持。

## 接下来的步骤

接下来，继续进行[Going Online](../going-online/)教程。

