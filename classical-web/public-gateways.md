# 课程:通过公共ipfs.io网关获取内容。

本课解释了如何从ipfs.io上的公共IPFS网关检索IPFS内容。在[与传统(HTTP) Web交互](./)的教程中对这个主题进行了更深入的讨论。

## 目标

学习完这节课，你就能

* 使用ipfs.io的公共网关访问IPFS的内容

## 怎么做

此过程与[使用任何其他IPFS网关](other-gateways.md)相同——只是网关的地址不同:如果你使用特定内容快照的哈希，请使用路径`https://ipfs.io/ipfs/<your-ipfs-hash>` 。如果你正在使用一个IPNS哈希来获取某些内容的最新版本，请使用路径`https://ipfs.io/ipns/<your-ipns-hash>` 。

要查看我们在所有课程中使用的wikipedia页面，请使用这些链接：

* 2017-04-30 snapshot: [http://ipfs.io/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](http://ipfs.io/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)
* latest \(IPNS\): [http://ipfs.io/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html](http://ipfs.io/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html) \[正确的例子，虽然这个链接可能过时了\]
* latest \(DNS\): [http://ipfs.io/ipns/ipfs.io](http://ipfs.io/ipns/ipfs.io)

## 解释

IPFS项目维护了公共IPFS网关，你可以使用这些网关访问来自IPFS网络的任何内容。当分享IPFS内容的HTTP链接时，人们经常使用ipfs.io地址，但是你可以使用任何网关的地址。

## 接下来的步骤

如果你想了解使用IPFS使用相同内容寻址链接访问相同内容的许多其他方法，请参阅[有关访问和分发IPFS内容的各种方法的教程](../avenues-for-access/)。

否则，继续下一课学习如何[通过任何IPFS网关访问IPFS内容](other-gateways.md)

