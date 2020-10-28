# 教程:访问和分发IPFS内容的各种方法

这些课程使用go-ipfs版本0.5.0进行了测试。 _请在github上更新这个文件，以反映已经测试过的其他版本。_

IPFS哈希是针对内容的永久性的、以内容寻址的标识符。这意味着你可以使用许多不同的方法来访问、复制和/或使用相同的链接/标识符重新分发相同的内容。本教程探索了许多实现此目的的方法。如果你想了解为什么拥有所有这些选项是有价值的，请阅读关于[内容寻址的力量](power-of-content-addressing.md)的课程。

\(基于 [https://en.wikipedia.org/wiki/Content\_addressable\_network](https://en.wikipedia.org/wiki/Content_addressable_network)\)

所有的课程都使用相同的内容:土耳其版维基百科的一个快照。

## 学习目标

这些课程会教你如何

* 定义 _内容寻址_ ，并将其与 _位置寻址_ 进行比较
* 使用IPFS内容哈希以多种方式访问同一个链接的相同内容
* 通过ipfs.io的公共IPFS网关访问内容
* 通过任何IPFS节点的http网关访问内容
* 使用IPFS浏览器扩展（browser extension）访问内容
* 通过Tor访问IPFS内容
* 使用一个sneakernet移动和重新分发IPFS内容
* 解释能够通过这么多不同路径访问IPFS内容的含义

## Lessons

1. 阅读 [内容寻址的力量](power-of-content-addressing.md)
2. 回顾[从一个peer那里检索内容]()的课程
3. 回顾一下关于与经典(HTTP) Web交互的教程中的这些课程
   * 回顾: [课程:使用一个HTTP浏览器从本地IPFS网关检索文件]()
   * 回顾: [课程:在ipfs.io上使用公共IPFS网关]()
   * 回顾: [课程:通过任何IPFS网关访问IPFS内容](../classical-web/other-gateways.md)
4. [课程:通过Tor网关（试验性的）访问IPFS内容](tor-gateways.md)
5. [课程:在Tor transport上运行IPFS(试验性的)](tor-transport.md)
6. [课程:通过一个浏览器扩展访问IPFS内容](browser-extension.md)
7. [课程:Sneakernets - 移动USB驱动器和其他硬件上的数据](sneakernets.md)

## 接下来的步骤

如果你想知道如何在共享后更新内容，请参阅教程:[在永久的Web上发布更改](../publishing-changes/)

如果你想了解IPFS如何使用Merkle DAG在内部存储这些内容，请访问[教程:Merkle树和IPFS DAG](../ipfs-dag/)

