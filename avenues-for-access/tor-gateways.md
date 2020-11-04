# 课程:通过Tor网关访问IPFS内容(试验性的)

## 目标

本课程介绍了通过Tor网关访问IPFS内容。

学习完这节课，你就能

* 使用Tor浏览器和Tor网络上的一个公共IPFS网关来访问IPFS内容

## 步骤

### 步骤1:下载Tor浏览器

如果你还没有安装Tor浏览器，请通过访问[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)从Tor项目下载Tor浏览器。

在一些国家，Tor项目网站被封锁或审查，无法直接下载Tor。Tor项目还在[Github上托管了Tor浏览器包](https://github.com/TheTorProject/gettorbrowser)的一个镜像。

[GetTor](https://www.torproject.org/projects/gettor)服务也可以用来下载Tor浏览器，当项目网站和镜像被阻止时。

### 步骤2:从IPFS-Tor网关请求所需的内容

`ipfs4uvgthshqonk.onion`是Tor网络上一个由志愿者运行的IPFS网关。你将使用此网关来请求IPFS内容。(警告:IPFS项目不运行此网关。我们不能保证稳定或安全。)在Tor网络上可能有许多其他IPFS网关。你可以通过这种方式使用它们中的任何一个 -- 只需把`ipfs4uvgthshqonk.onion`替换为你试图访问的网关名称。

在运行Tor浏览器时，输入要检索的IPFS内容的哈希。这部分与[使用任何其他IPFS网关](../classical-web/other-gateways.md)相同 -- 只是网关的地址不同:如果使用特定内容快照的哈希，请使用路径`https://ipfs4uvgthshqonk.onion/ipfs/<your-ipfs-hash>` 。如果你正在使用一个IPNS哈希来获取某些内容的最新版本，请使用路径`https://ipfs4uvgthshqonk.onion/ipns/<your-ipns-hash>` 。

要查看我们在所有课程中使用的wikipedia页面，请使用这些链接

* 2017-04-30 snapshot: [https://ipfs4uvgthshqonk.onion/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html](https://ipfs4uvgthshqonk.onion/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html)
* latest \(IPNS\): [https://ipfs4uvgthshqonk.onion/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html](https://ipfs4uvgthshqonk.onion/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html)
* latest \(DNS\): [https://ipfs4uvgthshqonk.onion/ipns/wikipedia-on-ipfs.io](https://ipfs4uvgthshqonk.onion/ipns/wikipedia-on-ipfs.io)
* \(你可以用[onion.link](https://onion.link)来验证它是否有效\)

## 解释

这种方法依赖于`ipfs4uvgthshqonk.onion`的IPFS网关为你从IPFS网络检索内容。与ipfs.io的网关相比，此网关的不同之处在于，它直接通过Tor协议监听请求。这允许你以匿名方式访问网关。

## 接下来的步骤

了解如何[配置一个IPFS节点使用Tor传输](tor-transport.md)或返回[多种方式访问和分发IPFS内容的教程](./)学习许多其他的方法可以使用IPFS访问相同的内容使用相同的内含寻址链接。

