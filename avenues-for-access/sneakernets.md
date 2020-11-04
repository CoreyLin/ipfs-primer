# 课程:Sneakernets - 移动USB驱动器和其他硬件上的数据

我们不是在开玩笑。如果你想通过[sneakernet](https://en.wikipedia.org/wiki/Sneakernet)在网络之间移动IPFS内容，IPFS是支持的。本课介绍了如何将IPFS内容加载到USB驱动器等存储设备上，这样你就可以将内容物理地移动到新的网络上，然后重新发布它。无需依赖网络之间的直接连接，这将使你的内容的IPFS链接在气隙（两个网络）的两边有效。

这是如何有用的例子:

* 在没有直接连接到internet主干网的地方(连接有限的偏远地点，空间站)提供internet内容
* 规避政府、公司和专横的审查。

对于本例，我们假设你正在使用一个外部驱动器将wikipedia的快照从IPFS移动到wikipedia不可用的一个新网络中。

## 先决条件

要做到这一课的步骤，你必须:

* 熟悉使用命令行
* 在本地机器上安装和初始化IPFS

## 目标

学习完本课程后，你将知道如何物理地跨网络移动IPFS内容，使其在另一端通过IPFS和HTTP可用。

## 步骤

### 步骤1:下载你想要移动的内容，以及IPFS的副本

使用`ipfs get`命令下载你想跨网络移动的内容。在本例中，我们将Wikipedia归档的一个完整快照下载到磁盘，并将其保存为一个名为WikipediaSnapshot的文件夹(警告:此快照为15 GB，你可能想用小一点的):

```bash
$ ipfs get Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html -o WikipediaSnapshot
```

还可以将最新的IPFS二进制文件下载到你的驱动器中。为了在另一边发布内容，你将需要这个。确保为要将数据移动到的计算机下载了适当的go-ipfs二进制文件。注意:当你阅读本文时，ipfs可能有一个更新版本。在[https://dist.ipfs.io/\#go-ipfs](https://dist.ipfs.io/#go-ipfs)可以找到最新的版本号

```bash
$ ipfs get /ipns/dist.ipfs.io/go-ipfs/v0.4.8 -o go-ipfs-v0.4.8
```

### 步骤2:复制文件到你的外部驱动器

* 复制快照(即文件夹“WikipediaSnapshot”)到你的外部驱动器
* 将下载的IPFS二进制文件(即文件夹“go-ipfs-v0.4.8”)复制到你的外部驱动器

### 步骤3:转到下一台电脑

* 弹出你的外部驱动器
* 将你的外部驱动器实际携带到你想要使用该信息的下一台计算机。

### 步骤4:在下一台计算机上安装IPFS并加载内容

首先在新计算机上安装并初始化IPFS二进制文件。[安装教程](../install-ipfs/)中的说明可能会有所帮助。

然后将数据导入ipfs(在本例中，是名为`WikipediaSnapshot`的文件夹)

```bash
$ ipfs add -r WikipediaSnapshot
```

### 步骤5:确认内容现在在新计算机上可用

启动ipfs daemon:

```bash
ipfs daemon
```

快照链接现在应该可以工作了: [http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)

## 解释

这种方法允许你物理地将IPFS内容移动到以前不可用的网络中。

因为IPFS使用内容寻址，所以只要添加到第二个网络的内容与最初从IPFS导出的原始内容相同，那么内容的IPFS标识符在两个网络中都是相同的。

## 接下来的步骤

返回[关于访问和分发IPFS内容的各种方法的教程](./)，了解使用IPFS使用相同内容寻址的链接访问相同内容的许多其他方法。

接下来，继续学习教程[对永久性Web进行更改](../publishing-changes/)。

