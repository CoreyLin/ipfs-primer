# 课程:向IPFS添加内容并检索它

## 目标

学习完这节课，你就能

* 将一个文件的内容添加到IPFS中
* 使用其哈希从IPFS中读取内容
* 解释IPFS哈希和你添加的内容之间的关系

## 步骤

### 步骤1:创建一个要添加到IPFS的文件

你可以向IPFS添加任何类型的内容。这节课我们将把一些文本内容放入`.txt`文件，但你可以对任何内容或任何文件执行相同的过程。

为这个示例创建一个新目录是个好主意。导航到你放置新文件夹的地方(比如`~/Desktop`)，然后创建一个新目录并进入其中。下面是一个示例命令:

```bash
$ cd ~/Desktop
$ mkdir ipfs-tutorial
$ cd ipfs-tutorial
```

现在，创建一个名为`mytextfile.txt`的文件，并将文本“version 1 of mytext”放入其中。在命令行上执行此操作的一种简单方法是使用以下命令

```bash
$ echo "version 1 of my text" > mytextfile.txt
```

你可以使用`cat`命令读取文件的内容

```bash
$ cat mytextfile.txt
version 1 of my text
```

### 步骤2:将文件添加到IPFS

```bash
$ ipfs add mytextfile.txt
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy mytextfile.txt
```

保存ipfs返回的哈希`QmZtmD2qt...`。这是内容的加密哈希。如果文件的内容改变了，哈希也会改变，但是如果文件的内容保持不变，哈希就会始终不变。

请记住，如果你没有[运行守护进程（daemon）](../going-online/connect-your-node.md#step-1-start-the-ipfs-daemon)，它只会在本地添加。如果你稍后启动守护进程（daemon），则在reprovider运行几秒钟后将公布这些blocks。

### 步骤3:从IPFS中读取内容

正如常规的`cat`命令允许你读取一个文件的内容一样，`ipfs cat`命令也允许你读取已添加到ipfs中的一个文件的内容。

使用`ipfs cat`命令通过传递内容的加密哈希来读取内容 -- 这是运行`ipfs add mytextfile.txt`时ipfs返回的哈希。

```bash
$ ipfs cat QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy
version 1 of my text
```

注意，这返回的是文件的内容，而不是文本文件本身。这是因为`QmZtmD2qt...`是内容的哈希，而不是文件本身。我们将在下一步测试它。

### 步骤4:确认哈希指向的是内容，而不是文件

当使用`ipfs cat`读取文件内容时，它返回文件的 _内容_ ，而不是文本文件本身。这是因为哈希值`QmZtmD2qt...`是 _内容_ 的哈希。你可以通过将文本内容直接添加到IPFS而不将其放入文件来测试。

```bash
$ echo "version 1 of my text" | ipfs add
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy
```

这个哈希应该与你添加mytextfile.txt时得到的哈希完全相同。如果你想要进行三重检查，那么你可以任意多次运行这些命令。哈希应该总是相同的。

```bash
$ ipfs add mytextfile.txt
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy mytextfile.txt
$ echo "version 1 of my text" | ipfs add
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy
$ cat mytextfile.txt | ipfs add
added QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy
```

只要内容保持不变，你将始终得到相同的哈希。就IPFS而言，内容 _是_ 相同的。

### 步骤5:更改内容并获得不同的哈希

现在将文本内容更改为“version 2 of my text”并添加到ipfs中。你会得到一个不同的哈希。

正如你在上一步中确认的那样，你可以将新文本直接添加到IPFS中，也可以修改mytextfile.txt并将其添加到IPFS中。你会得到相同的哈希值。

```bash
$ echo "version 2 of my text" | ipfs add
added QmTudJSaoKxtbEnTddJ9vh8hbN84ZLVvD5pNpUaSbxwGoa QmTudJSaoKxtbEnTddJ9vh8hbN84ZLVvD5pNpUaSbxwGoa
```

### 步骤6:将内容从IPFS传输到一个文件中

你可以从ipfs中读取此内容(任何版本)并将其写入一个文件。例如，你可以切换mytextfile.txt的内容从“版本1”到“版本2”以及切换回来，运行你想要的任何次数。

```bash
$ ipfs cat QmTudJSaoKxtbEnTddJ9vh8hbN84ZLVvD5pNpUaSbxwGoa > mytextfile.txt
$ cat mytextfile.txt
version 2 of my text
$ ipfs cat QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy > mytextfile.txt
$ cat mytextfile.txt
version 1 of my text
```

还可以将ipfs中的内容写入一个全新的文件中。

```bash
$ ipfs cat QmZtmD2qt6fJot32nabSP3CUjicnypEBz7bHVDhPQt9aAy > anothertextfile.txt
$ cat anothertextfile.txt
version 1 of my text
```

## 解释

IPFS根据其加密哈希跟踪内容。**这个哈希准确地唯一地标识该内容。**只要内容保持不变，哈希就保持不变。如果内容改变，你将得到一个不同的哈希。

如果你有两个包含相同内容的不同文件，IPFS将使用一个哈希跟踪该内容。文件名不同，但内容是相同的，因此内容的哈希是相同的。

这就引出了一个问题:IPFS如何跟踪文件名?这是下节课的主题。

## 下一课:将文件名和目录信息添加到IPFS

继续下一课，学习如何[在IPFS中围绕内容包装文件名和目录信息](wrap-directories-around-content.md)

