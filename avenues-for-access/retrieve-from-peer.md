# 从一个peer检索内容

本课演示如何使用你的计算机上的IPFS节点从网络上的其他peers请求内容。关于[IPFS上的文件](https://github.com/CoreyLin/ipfs-primer/tree/bab50d1b22ae297b07c3c7d729b0ad2ba500b795/going-online/lessons/files-on-ipfs/README.md)的教程将更深入地讨论一些基础主题。

## 先决条件

要做到这一课的步骤，你必须:

* 熟悉使用命令行
* 在本地机器上安装和初始化IPFS

## 目标

学习完这节课，你就能

* 使用命令行接口通过你本地IPFS节点访问任何内容

## 步骤

### 步骤1:启动IPFS daemon

通过以下命令启动IPFS daemon

```bash
$ ipfs daemon
```

如果daemon没有运行，你的IPFS节点将不能从网络上的其他节点检索内容。

### 步骤2:通过命令行读取内容

你可以使用命令行从你的IPFS节点请求内容。如果节点没有该内容的副本，它将尝试寻找具有该内容的另一个peer节点。例如，IPFS团队发[布了土耳其版维基百科的一个快照](https://ipfs.io/blog/24-uncensorable-wikipedia/)。该快照的哈希包含大约15GB的土耳其语维基百科页面，它是`Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1`。我们可以使用命令行让IPFS节点从该快照读取页面。

```text
# get the article about "Peer to Peer"
ipfs cat Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Peer-to-peer.html > Peer-to-peer.html

# explore the articles in the snapshot
ipfs ls -v -s Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/
```

如果你不熟悉`ipfs cat`和`ipfs ls`命令，在[关于IPFS上的文件的教程](../files-on-ipfs/)中对它们进行了解释。

## 解释

你可以使用一个本地IPFS节点从全球IPFS网络读取内容。一种方法是通过命令行使用像`ipfs cat`和`ipfs ls`这样的命令。当你将所需内容的以内容寻址(哈希)标识符传递到这些命令时，IPFS节点将检查它是否拥有你所请求的内容的本地副本。如果你的节点有本地副本，它将立即返回该内容给你。如果你的节点没有本地副本，它将尝试在IPFS网络上找到具有该内容的一个peer。只要至少有一个peer拥有你想要的内容，你的IPFS节点就能够找到该peer，从该peer检索内容，并将该内容返回给你。

这是一个IPFS节点的基本功能。它使用内容寻址(哈希)标识符查找点对点网络上的内容。它还将该内容提供给其他需要它的peers。

## 接下来的步骤

本课介绍了如何使用命令行从你的IPFS节点请求内容，但是还有许多其他与IPFS节点交互的方法。如果你想了解使用IPFS使用相同内容寻址链接访问相同内容的许多其他方法，请参阅[有关访问和分发IPFS内容的各种方法的教程](./)。

否则，继续下一课[与传统(HTTP) Web交互](../classical-web/)

