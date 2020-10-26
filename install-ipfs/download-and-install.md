# 课程:下载并安装IPFS

## 目标

学习完这节课，你就能

* 下载IPFS并将其安装到操作系统上
* 显示你正在使用的IPFS版本
* 获取ipfs二进制文件支持的命令列表

## 步骤

### 步骤1:下载预构建的IPFS包

通过 [https://docs.ipfs.io/guides/guides/install/](https://docs.ipfs.io/guides/guides/install/) 访问IPFS安装页面，并下载针对你的操作系统预构建的ipfs二进制文件。

**为什么安装页面要说到“Go IPFS”?**IPFS协议有多种实现。IPFS的核心团队用Golang和Javascript实现。它们通常被称为 [go-ipfs](https://github.com/ipfs/go-ipfs) 和 [js-ipfs](https://github.com/ipfs/js-ipfs) 。官方二进制文件是从Go实现构建的。

### 步骤2:解压缩预先构建的包

Mac OSX和Linux的二进制文件采用gzipped tar格式(.tar.gz)。Windows的二进制文件在一个zip文件中。使用适当的工具解压缩文件。在 [https://docs.ipfs.io/guides/guides/install/](https://docs.ipfs.io/guides/guides/install/) 上标题 _Installing from a Prebuilt Package_下有一些提示。

这将创建一个名为go-ipfs的目录。

```bash
LICENSE        README.md    build-log    install.sh ipfs
```

名为`ipfs`的文件是可执行的ipfs二进制文件。

### 步骤3:在可执行路径上安装IPFS二进制文件

要安装二进制文件，所有你所需要做的就是将`ipfs`二进制文件放在可执行路径的某个位置。

**注意权限**:无论你使用何种方式安装二进制文件，请确保你拥有必要的权限。在Mac OSX或Linux上，你可能想使用 [sudo](https://www.sudo.ws/) ，它已经安装在大多数系统上。

如果你使用的是Mac OSX或Linux，则可以通过运行提供的安装脚本

```bash
cd go-ipfs
sudo ./install.sh
```

读取运行它的输出。如果它抱怨无法写入文件，那么你需要处理权限(参见上面关于权限的说明)

### 步骤4:显示IPFS版本

在进行故障排除时，一定要知道使用的是ipfs的哪个版本。要找出当前版本，请运行

```bash
$ ipfs version
```

### 步骤5:显示IPFS帮助页面和命令列表

如果你需要帮助来记住如何使用ipfs命令，请运行

```bash
$ ipfs help
```

这应该显示以如下开头的信息

```bash
USAGE:

    ipfs - Global p2p merkle-dag filesystem.
...
```

要获得ipfs可执行文件支持的命令的完整列表，请运行

```bash
$ ipfs commands
```

## 接下来的步骤

接下来, [初始化IPFS仓库](initialize-repository.md)

