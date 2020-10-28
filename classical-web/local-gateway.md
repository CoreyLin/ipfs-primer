# 课程:使用HTTP浏览器从本地IPFS网关检索文件

本课展示了通过本地安装在计算机上的一个IPFS节点访问内容的一些不同方法。在关于[IPFS上的文件](../files-on-ipfs/)和[Going Online - 加入分布式Web](../going-online/)的教程中，更深入地讨论了一些基本主题。

## 先决条件

要做到这一课的步骤，你必须:

* 在本地机器上[安装和初始化IPFS](../install-ipfs/)

## 目标

学习完这节课，你就能

* 通过你本地IPFS节点的HTTP网关访问任何内容

## 步骤

### 步骤1:启动IPFS daemon

通过运行以下命令启动IPFS daemon

```bash
$ ipfs daemon
```

如果daemon没有运行，你的IPFS节点将不能从网络上的其他节点检索内容。它也不会启动你将在步骤2中使用的HTTP网关。

### 步骤2:通过你的IPFS节点的HTTP网关读取请求内容

你必须告诉网关你是使用一个IPFS哈希还是一个IPNS哈希请求内容。如果使用内容的一个特定快照的哈希(例如某人添加到IPFS的一个文件)，请使用以`/ipfs/`开头的路径。如果你正在使用一个IPNS哈希来获取随着时间的推移而更新的某些内容的最新版本，例如每天更新内容的一个网站，请使用一个以`/ipns/`开头的路径。

要查看我们在所有课程中使用的wikipedia页面，请使用以下链接:

* 2017-04-30 snapshot: [http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)
* latest \(IPNS\): [http://localhost:8080/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html](http://localhost:8080/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html) \[正确的例子，虽然这个链接可能过时了\]
* latest \(DNS\): [http://localhost:8080/ipns/ipfs.io](http://localhost:8080/ipns/ipfs.io)

## 解释

你可以使用一个本地IPFS节点从全球IPFS网络读取内容。与你的本地节点交互的两种方式是1)通过命令行和2)通过HTTP网关。可以使用任一接口向IPFS传递所需内容的内容寻址(哈希)标识符。IPFS节点将使用这些标识符在网络上查找内容并为你检索它。

## 接下来的步骤

如果你想了解使用IPFS使用相同内容寻址链接访问相同内容的许多其他方法，请参阅[有关访问和分发IPFS内容的各种方法的教程](../avenues-for-access/)。

否则，继续下一课学习如何[通过公共ipfs.io网关获取内容]()。

