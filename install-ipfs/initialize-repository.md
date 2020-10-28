# 课程:初始化IPFS仓库

## 目标

学习完这节课，你就能

* 初始化一个本地ipfs仓库
* 找到IPFS存储本地IPFS仓库内容的位置
* 打开IPFS配置文件

## 步骤

### 步骤1:初始化仓库

使用`ipfs init`命令初始化仓库。这将为你机器上的当前用户帐户生成一个本地ipfs仓库。它还生成一个加密密钥对（keypair），允许ipfs节点以加密方式对所创建的内容和消息进行签名。

```bash
$ ipfs init
initializing ipfs node at /Users/jbenet/.go-ipfs
generating 2048-bit RSA keypair...done
peer identity: Qmcpo2iLBikrdf1d6QU6vXuNb6P7hwrbNPW9kLAH8eG67z
to get started, enter:

  ipfs cat /ipfs/QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/readme
```

 **注意:** 如果你已经在你的机器上初始化了ipfs，你将得到一个错误消息，如

```text

initializing ipfs node at /Users/sally/.ipfs
Error: ipfs configuration file already exists!
Reinitializing would overwrite your keys.
```

 这是ok的。这意味着你已经完成了这一步。你可以安全地继续第2步。

### 步骤2:使用IPFS查看安装后文档

 如果你安装了一个不同版本的ipfs，那么在这里使用的路径可能略有不同。每种路径都适用于本教程。从ipfs init命令获得的路径将为你提供适合你正在使用的ipfs版本的文档。

当你运行ipfs init时，它提供了如何开始的提示。它说:

```bash
to get started, enter:

  ipfs cat /ipfs/QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/readme
```

这个`ipfs cat`命令告诉ipfs读取与你提供的路径匹配的内容。如果内容在本地找不到，ipfs将尝试在点对点网络上找到它。

为了运行以下命令，ipfs守护进程必须运行。要运行ipfs守护进程，输入`ipfs daemon &`。这将启动ipfs守护进程，并将其放到当前控制台的背景中。

```bash
$ ipfs daemon &
```

使用从init消息获得的路径运行`ipfs cat`命令

```bash
$ ipfs cat /ipfs/QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/readme
```

你应该看到这样的东西:

```text
Hello and Welcome to IPFS!

██╗██████╗ ███████╗███████╗
██║██╔══██╗██╔════╝██╔════╝
██║██████╔╝█████╗  ███████╗
██║██╔═══╝ ██╔══╝  ╚════██║
██║██║     ██║     ███████║
╚═╝╚═╝     ╚═╝     ╚══════╝

If you're seeing this, you have successfully installed
IPFS and are now interfacing with the ipfs merkledag!

 -------------------------------------------------------
| Warning:                                              |
|   This is alpha software. use at your own discretion! |
|   Much is missing or lacking polish. There are bugs.  |
|   Not yet secure. Read the security notes for more.   |
 -------------------------------------------------------

Check out some of the other files in this directory:

  ./about
  ./help
  ./quick-start     <-- usage examples
  ./readme          <-- this file
  ./security-notes
```

你可以在其中探索其他对象。例如，访问`security-notes`

```bash
ipfs cat /ipfs/QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/security-notes
```

### 步骤3:定位IPFS在你的机器上存储仓库内容的位置

`ipfs`将其本地对象仓库存储在`~/.ipfs`中

```bash
$ ls ~/.ipfs
```

该目录的内容如下所示:

```bash
blocks        config        datastore    version
```

IPFS仓库的所有内容都存储在这个目录中。例如，上面的readme文件和它链接的其他文件一起存储在这里。你可以运行grep来找出确切的位置。

### 步骤4:打开IPFS配置文件

ipfs仓库的配置在一个json文件中，该文件通常存储在`~/.ipfs/config`中。要查看当前配置，请运行:

```bash
$ ipfs config show
```

这个配置文件中有用的细节之一是`Datastore.Path`。这将告诉你ipfs仓库的内容存储在何处。正如我们在步骤3中看到的，这通常是`~/.ipfs`

## 接下来的步骤

下一步，进入[IPFS上的文件](../files-on-ipfs/)教程

