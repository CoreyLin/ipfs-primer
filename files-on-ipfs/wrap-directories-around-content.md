# 课程:围绕内容包装文件名和目录信息

## 目标

学习完这节课，你就能

* 向IPFS中添加一个文件，包括它的文件名、权限等。
* 向IPFS添加目录
* 解释IPFS如何表示具有相同内容的两个文件
* 使用包含文件的一个目录的哈希从IPFS中读取内容

## 步骤

### 步骤1:创建要添加的文件

你可能已经从上一课中获得了这个文件。请确保文件的内容匹配。否则你得到的哈希值将与本课的例子不符。

创建一个名为`mytextfile.txt`的文件，并将文本“version 1 of mytext”放入其中。这里有一个简单的命令行方法来做这个:

```bash
$ echo "version 1 of my text" > mytextfile.txt
```

### 步骤2:将文件添加到IPFS

```bash
$ ipfs add -w mytextfile.txt
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy mytextfile.txt
added QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w
```

在上一课中，当运行`ipfs add mytextfile.txt`不带`-w`标志时，ipfs只返回一个哈希。这次它返回了两个哈希值。第一个哈希值`QmZtmD2...`与之前相同—它是文件内内容的哈希。第二个哈希值`QmPvaEQF...`是目录和文件名信息的哈希，ipfs用来“包装”我们的内容。

在接下来的步骤中，你将使用ipfs命令查看目录和文件名信息以及如何使用它。

### 步骤3:列出目录信息

`-w`标志告诉ipfs在和内容一起包含目录和文件名信息——它“将文件包装在一个目录中”。要了解更多信息，请运行`ipfs add -help`并阅读那里的描述。

要列出这个目录和文件名信息，请使用`ipfs ls`。你将使用`-v`标志来包含header信息。要了解关于此命令的更多信息，请运行`ipfs ls --help`。

```bash
$ ipfs ls -v QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w
Hash                                           Size Name
QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy 29   mytextfile.txt
```

这个命令`ipfs ls QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w`翻译为“列出这个目录引用的文件，该目录的哈希值是QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w”。

响应显示该目录包含一个文件— "mytextfile.txt" —以及该文件内容的哈希值为`QmZtmD2q...`。

请注意，你必须使用`ipfs ls`而不是`ipfs cat`来读取此信息，因为它是一个目录。如果你尝试使用`ipfs cat`读取目录，你会得到一个错误:

```text

$ ipfs cat QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w
Error: this dag node is a directory
```

### 步骤4:使用父目录的哈希读取文件的内容

你可以像这样使用目录的哈希来读取文件的内容

```bash
$ ipfs cat QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w/mytextfile.txt
version 1 of my text
```

这个命令翻译为“返回目录中称为`mytextfile.txt`的内容，该目录的哈希值为QmPvaEQFVvuiaYzkSVUp23iHTQeEUpDaJnP8U7C3PqE57w。

## 额外的步骤

有些事情可以尝试:

1. 创建一个包含多个文件的目录。告诉ipfs递归地添加目录及其所有文件。
2. 创建两个具有相同内容的不同文件。使用`ipfs add -w`将它们都添加到ipfs中，并确认ipfs在构建目录和文件名信息时重用了该内容的哈希。

## 解释

当你将一个文件添加到ipfs仓库时，ipfs计算文件内容的加密哈希，并将该哈希返回给你。然后可以使用该哈希引用文件的内容，并将它们从ipfs仓库中读取出来。

为了跟踪文件名和路径之类的信息，ipfs允许在添加的文件内容周围“包装”目录和文件名信息。目录和文件名信息有自己的哈希。这使得使用“ipfs paths”从ipfs仓库检索内容成为可能，“ipfs paths”是哈希、文件名和目录名的组合。

## 接下来的步骤

接下来，学习如何[告诉IPFS保存一个文件](pin-files.md)

