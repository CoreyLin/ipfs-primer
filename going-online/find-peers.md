# 课程:在网络上寻找Peers

本课展示了如何查找和检查IPFS网络上连接的peers。为此，你将使用`ipfs swarm`和`ipfs id`工具。swarm是一个打开、监听和维护与其他IPFS peers连接的组件。你还可以使用Web UI检查连接的peers和网络。

## 先决条件

要做到这一课的步骤，你必须:

* 正在运行`ipfs daemon`

## 目标

学习完这节课，你就能

* 查找和检查IPFS网络中的peers

## 步骤

### 步骤1:启动IPFS daemon

通过运行如下命令启动IPFS daemon

```bash
$ ipfs daemon
```

### 步骤2:找到与我们连接上的peers

你可以使用命令`ipfs swarm peers`检查连接上的peers:

```bash
$ ipfs swarm peers
/ip4/147.75.69.143/tcp/4001/ipfs/QmNn....GAJN
/ip4/147.75.83.83/tcp/4001/ipfs/QmbL....75Nb
/ip4/147.75.85.167/tcp/4001/ipfs/QmXA....qhfW
/ip6/2604:1380:0:c100::1/tcp/4001/ipfs/QmQC....uLTa
/ip6/2604:1380:3000:1f00::1/tcp/4001/ipfs/QmcZ....3dwt
/ip6/2604:1380:40b0:c00::3/tcp/4001/ipfs/QmYA....yYdN
```

### 步骤3:检查连接的一个peer

你将使用`ipfs id <hash>`命令检查连接的一个peer

```bash
$ ipfs id Qmf1...mx36
{
    "ID": "Qmf1....mx36",
    "PublicKey": "CAAS....AAE=",
    "Addresses": [
        "/ip4/127.0.0.1/tcp/4001",
        "/ip6/::1/tcp/4001",
        "/ip4/134.215.4.214/tcp/4001"
    ],
    "AgentVersion": "go-ipfs/0.4.21/8ca278f45",
    "ProtocolVersion": "ipfs/0.1.0"
}
```

注意:上面显示的“ID”字段是peer的ID，这也是运行`ipfs swarm peers`时显示的哈希。在网络上通过peer ID直接识别peers。

### 步骤4:用Web UI来检查

IPFS daemon还提供了一个可以在浏览器中打开的现代Web UI。你是否注意到在启动deamon时存在以下信息?

WebUI: [http://127.0.0.1:5001/webui](http://127.0.0.1:5001/webui)

在你的浏览器中打开上面的链接。你将看到Web UI显示状态、文件、浏览、Peers和设置部分。单击“Peers”部分，你将看到一张指示连接的peers的位置的世界地图。向下滚动页面可以看到每个peer的信息，它们的国家/城市位置，网络延迟，Peer ID，等等。花点时间看看Web UI的其他不同部分。

## 解释

通过运行daemon连接到IPFS网络之后，其他IPFS节点(peers)将开始与你的节点连接和通信。使用命令`ipfs swarm`和`ipfs id`可以检查连接的节点。Web UI还显示了关于peers的深入信息。

## 下一课:从一个peer那里检索内容

继续下一课，学习如何[从一个peer检索内容]

