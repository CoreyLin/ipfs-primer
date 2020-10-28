# 教程:IPFS上的文件

这些课程使用go-ipfs版本0.5.0进行了测试。 _请在github上更新这个文件，以反映已经测试过的其他版本。_

## 先决条件

* 你应该对命令行有一些熟悉。
* 你应该安装了`ipfs` - [上一教程](../install-ipfs/)对此有说明

## 学习目标

这些课程会教你如何

* 将文件添加到本地IPFS节点
* 从本地IPFS节点读取文件
* 列出IPFS节点中的文件
* 告诉IPFS通过 _pin_ 来保存文件

## 关键概念

* IPFS和常规文件系统之间的区别
* 通过哈希识别文件
* IPFS垃圾收集
* 将文件pin在一个IPFS节点上

## 课程

1. [课程:向IPFS添加内容并检索它](add-and-retrieve-file-content.md)
2. [课程:将文件名和目录信息围绕在IPFS的内容周围](wrap-directories-around-content.md)
3. [课程:Pinning - 让IPFS保存一个文件](pin-files.md)

## 接下来的步骤

一旦你了解了如何将文件添加到IPFS并检索它们，你就可以按照[Tutorial: Going Online - Joining the Distributed Web](../going-online/)在P2P网络上共享这些文件了。

如果你想知道如何在共享这些文件后更新它们，请参阅[Tutorial: Publishing Changes on the Permanent Web](../publishing-changes/)

如果你想了解如何从传统HTTP web访问这些文件，请参阅[Tutorial: Interacting with the Classical \(HTTP\) Web](../classical-web/)

如果你想了解更多关于IPFS如何使用Merkle DAG在内部存储这些内容，请访问[Tutorial: Merkle Trees and the IPFS DAG](../ipfs-dag/)

