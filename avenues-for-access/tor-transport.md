# 课程:在Tor transport上运行IPFS(试验性的)

IPFS有一个实验性的特性，允许一个IPFS节点通过Tor传输协议与其他IPFS节点交互。这个特性的目标是允许IPFS节点之间匿名通信。 **这个特性是实验性的!** 在我们测试了此特性并删除了“实验性”名称之前，你应该假定有关你的节点的信息可能会泄漏。

与此同时，一种更安全的保护匿名性的方法是[使用tor浏览器和一个IPFS tor网关访问数据](tor-gateways.md)。

## 先决条件

要做到这一课的步骤，你必须:

* 熟悉使用命令行
* 在本地机器上安装和初始化IPFS

## 目标

学习完这节课，你就能

* 将一个IPFS节点配置为使用Tor传输
* 通过该节点请求内容

## 步骤

### 步骤1:配置IPFS以使用Tor传输

Work-In-Progress: [https://github.com/ipfs/notes/issues/37](https://github.com/ipfs/notes/issues/37)

Work-In-Progress: [https://github.com/OpenBazaar/go-onion-transport](https://github.com/OpenBazaar/go-onion-transport)

TODO - 这个解释还没有写出来。如果你想帮助解决这个问题，或者你想鼓励我们关注这个问题，在[https://github.com/ipfs-shipyard/ipfs-primer/issues](https://github.com/ipfs-shipyard/ipfs-primer/issues)上开一个issue。

### 步骤2:启动IPFS daemon

启动IPFS daemon

```bash
$ ipfs daemon
```

有关这一步的更多信息，请阅读[教程:Going Online - 加入分布式Web](../going-online/)

### 步骤3:从你的本地IPFS节点的网关请求所需的内容

此步骤与[使用任何其他IPFS网关](../classical-web/other-gateways.md)相同 -- 只是网关的地址不同:如果使用特定内容快照的哈希，请使用路径`http://localhost:8080/ipfs/<your-ipfs-hash>` 。如果使用一个IPNS哈希来获取某些内容的最新版本，请使用路径`http://localhost:8080/ipns/<your-ipns-hash>` 。

要查看我们在所有课程中使用的wikipedia页面，请使用这些链接

* 2017-04-30 snapshot: [http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](http://localhost:8080/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)
* latest \(IPNS\): [http://localhost:8080/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html](http://localhost:8080/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html)
* latest \(DNS\): [http://localhost:8080/ipns/wikipedia-on-ipfs.io](http://localhost:8080/ipns/wikipedia-on-ipfs.io)

## 解释

**这个特性是实验性的!** 在我们测试了这个特性并去掉了“实验性”的名称之前，你应该假设这里的解释是期望的和临时的。我们正在描述什么应该是真实的，但我们还没有测试和确认这种方法在没有泄露信息的情况下工作。

当你将一个IPFS节点配置为使用Tor传输时，该节点将通过Tor onion网络传输它的所有点对点通信。这意味着，当你从你的本地节点请求内容时，无论是通过它在localhost:8080上的http网关还是通过命令行，节点都将通过tor传输协议访问IPFS网络。当它与IPFS网络上的peers连接时，peers将不知道它们正在与哪个节点通信，也不知道它在哪里。

## 接下来的步骤

返回[关于访问和分发IPFS内容的各种方法的教程](./)，了解使用IPFS使用相同内容寻址的链接访问相同内容的许多其他方法。

