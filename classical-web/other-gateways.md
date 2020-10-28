# 课程:通过任何IPFS网关访问IPFS内容

## 目标

本课将介绍如何使用任何IPFS网关访问IPFS内容。本文简要回顾了[使用HTTP浏览器从一个本地IPFS网关检索文件的经验]()

学习完这节课，你就能

* 使用任何IPFS网关的HTTP地址来访问IPFS内容

## 步骤

### 步骤1:获取一个网关的地址

正如我们在教程:[Going Online - 加入分布式Web](../going-online/)中所述，当你运行一个IPFS daemon时，它将公开一个HTTP端点，该端点充当HTTP和IPFS网络之间的一个网关。这意味着从理论上讲，你可以将web浏览器指向任何IPFS节点的HTTP端点，并将其用作一个网关。实际上，运行该节点的人通常需要采取额外的步骤(NAT穿透等)，以使他们的网关通过HTTP可用。

对于这些示例，我们将使用`http://dweb.link`上的网关

### 步骤2:建立通往内容的路径

正如在[使用HTTP浏览器从本地IPFS网关检索文件]()这一课中所描述的，你必须告诉网关你是使用一个IPFS哈希还是一个IPNS哈希请求内容。如果你正在使用内容的一个特定快照的哈希(例如某人添加到IPFS的一个文件)，请使用路径`/ipfs/<your-ipfs-hash>` 。如果你正在使用一个IPNS哈希来获取一些随着时间而更新的内容的最新版本，例如一个每天都更新内容的网站，使用路径`/ipns/<your-ipns-hash>` 。

### 步骤3:从网关请求内容

结合网关的地址(例如`http://dweb.link`)和到内容的路径（如`/ipfs/<your-ipfs-hash>`）。使用它来请求内容。

要查看我们在所有课程中使用的wikipedia页面，请使用这些链接

* 2017-04-30 snapshot: [http://dweb.link/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](http://dweb.link/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)
* latest \(IPNS\): [http://dweb.link/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html](http://dweb.link/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html) \[正确的例子，虽然这个链接可能过时了\]
* latest \(DNS\): [http://dweb.link/ipns/ipfs.io](http://dweb.link/ipns/ipfs.io)

## 解释

在上面的示例中，我们使用internet上的一个HTTP连接，连接到提供到IPFS网络的网关的某个人(`http://dweb.link`)。通过这种方式，你可以访问IPFS网络中的信息，并且不需要运行自己的IPFS网关。

TODO

* 限制你的网关将服务的内容
* 安全问题——网关可以看到一个HTTP服务器可以看到的所有内容。

## 接下来的步骤

如果你想了解使用IPFS使用相同内容寻址链接访问相同内容的许多其他方法，请参阅[有关访问和分发IPFS内容的各种方法的教程](../avenues-for-access/)。

否则，返回到关于[与传统(HTTP) web交互](./)的教程

