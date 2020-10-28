# 课程:将你的节点连接到IPFS网络

这节课展示了如何将本地计算机上的IPFS节点连接到IPFS网络，或称为“swarm”。到目前为止你所做的一切都是在本地完成的。现在它变得有趣多了!

## 先决条件

要做到这一课的步骤，你必须:

* 熟悉使用命令行
* 在本地机器上[安装和初始化IPFS](../install-ipfs/)

## 目标

学习完这节课，你就能

* 启动IPFS daemon，将本地节点连接到IPFS网络

## 步骤

### 步骤1:启动IPFS daemon

通过运行以下命令启动IPFS daemon

```bash
$ ipfs daemon
```

你将看到daemon的输出，如下所示

```bash
Initializing daemon...
go-ipfs version: 0.5.0-dev-17e886e29
Repo version: 7
System version: amd64/linux
Golang version: go1.13.5
Swarm listening on /ip4/12.2.0.36/tcp/4001
Swarm listening on /ip4/127.0.0.1/tcp/4001
Swarm listening on /ip6/::1/tcp/4001
Swarm listening on /p2p-circuit
Swarm announcing /ip4/12.2.0.36/tcp/4001
Swarm announcing /ip4/127.0.0.1/tcp/4001
Swarm announcing /ip6/::1/tcp/4001
API server listening on /ip4/127.0.0.1/tcp/5001
WebUI: http://127.0.0.1:5001/webui
Gateway (readonly) server listening on /ip4/127.0.0.1/tcp/8080
Daemon is ready
```

请注意，如果你在运行daemon之前[add了文件](../files-on-ipfs/add-and-retrieve-file-content.md)，那么当reprovider运行几秒钟后，就会公布这些blocks。

### 步骤2:检查你的ipfs节点id信息

让我们通过`ipfs id`看看这个daemon创建的连接的细节。打开另一个命令行并运行：

```bash
$ ipfs id
{
    "ID": "QmRX....xQTp",
    "PublicKey": "CAAS....AAE=",
    "Addresses": [
        "/ip4/127.0.0.1/tcp/4001/ipfs/QmRX....xQTp",
        "/ip4/12.2.0.36/tcp/4001/ipfs/QmRX....xQTp",
        "/ip6/::1/tcp/4001/ipfs/QmRX....xQTp",
        "/ip6/2802:285:8360:da70::9191/tcp/4001/ipfs/QmRX....xQTp",
        "/ip6/2802:285:8360:da70:5146:9a0a:e910:19c3/tcp/4001/ipfs/QmRX....xQTp",
        "/ip6/2802:285:8360:da70:ccb4:bd10:baa3:d022/tcp/4001/ipfs/QmRX....xQTp",
        "/ip4/83.24.208.218/tcp/26521/ipfs/QmRX....xQTp"
    ],
    "AgentVersion": "/go-ipfs/0.5.0-dev/17e886e29",
    "ProtocolVersion": "ipfs/0.1.0"
}
```

注意:为了可读性，上面的哈希被缩短了。

“ID”字段是你的Peer ID，用于在IPFS网络上唯一地标识你的节点。“PublicKey”字段与你的Peer ID一起使用，IPFS在底层使用它进行公钥加密。显示的“Addresses”是用于IPFS网络通信的IP地址数组。使用TCP端口4001的地址称为“swarm addresses”，你的本地daemon将用这些地址监听来自其他IPFS peers的连接。

### 步骤3:关闭daemon

你可以通过在你开始的命令行输入Ctrl-C来关闭daemon:

```bash
...
Daemon is ready
^C
Received interrupt signal, shutting down...
(Hit ctrl-c again to force-shutdown the daemon.)
```

注意:你可以使用命令`ipfs daemon &`作为后台进程运行IPFSdaemon。如果您想停止后台进程，只需键入`fg`(前台)将该进程放到前台，然后按Ctrl-C停止它。

```bash
$ ipfs daemon &
pid 8469
$ Initializing daemon...
go-ipfs version: 0.5.0-dev-17e886e29
Repo version: 7
System version: amd64/linux
Golang version: go1.13.5
Swarm listening on /ip4/10.0.0.35/tcp/4001
...
Gateway (readonly) server listening on /ip4/127.0.0.1/tcp/8080
Daemon is ready
fg
ipfs daemon
^C
Received interrupt signal, shutting down...
(Hit ctrl-c again to force-shutdown the daemon.)
```

## 解释

运行IPFS daemon是为了让本地IPFS节点成为IPFS网络的一部分，并监听其他IPFS peers。

## 下一课:在网络上寻找Peers

继续下一课，学习如何[在网络上查找Peers](find-peers.md)

