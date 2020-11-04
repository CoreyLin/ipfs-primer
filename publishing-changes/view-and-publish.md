# 课程:用IPFS查看你的网页并发布到IPNS上

这节课将向你展示如何查看添加到IPFS中的一个简单网页，以及如何将该网页发布到IPNS中。

## 目标

学习完这节课，你就能

* 查看你之前创建的简单网页，并将其发布到IPNS

## 步骤

### 步骤1:使用IPFS哈希查看你的网页

当你在上一课中运行`ipfs add -r simple-webpage/`命令时，你的输出如下:

```bash
added Qmd286K6pohQcTKYqnS1YhWrCiS4gz7Xi34sdwMe9USZ7u simple-webpage/cat.jpg
added QmNiBYXmgwLvT4xBiL8cX9j5H3AckiEjAnLZsoBiK6xEEr simple-webpage/index.html
added QmZhCL5rkWjH4MotDxKHUDaUESEKhTxSE7Xr16zwe59sjT simple-webpage
 432.98 KiB / 432.98 KiB [=============================================] 100.00%
```

最后一行的IPFS哈希是用于查看网页的哈希。注意，你自己的哈希可能不同。使用你的IPFS哈希并在浏览器中打开你的网页，如下所示:

`https://ipfs.io/ipfs/your-webpage-hash`

你应该看到上一课的“漂亮猫咪”网页。

### 步骤2:发布你的网页到IPNS

太棒了，现在你可以通过IPFS访问你的网页了。但假如你决定修改这个网页呢?上面的IPFS哈希只会指向你的网页的第一个版本。通过使用IPNS(星际名称系统)，你可以创建一个不会改变的哈希，但是你将使它指向IPFS中更改的内容。IPNS哈希将绑定到你的Peer ID，未来的任何更改也将绑定到你的Peer ID。

运行以下命令(使用你的网页哈希)发布到IPNS:

```bash
$ ipfs name publish your-webpage-hash
```

你应该看到如下所示的输出

```bash
Published to QmRX....xQTp: (your peer id)
/ipfs/QmZh....your-webpage-hash....9sjT
```

请注意，第一行的哈希将是你的Peer ID。使用IPNS时，你已经将Peer ID绑定到先前添加到IPFS的网页上。你可以使用以下命令确认你的Peer ID绑定到该IPFS条目:

```bash
$ ipfs name resolve your-peer-id
```

你应该看到如下所示的输出

```bash
/ipfs/your-webpage-hash
```

现在，你将能够使用你的Peer ID的一个IPNS链接来查看该网页:

`https://ipfs.io/ipns/your-peer-id`

请注意，一旦发布到IPNS, URL是如何从`/ipfs/`更改为`/ipns/`的。

## 解释

网页的IPFS哈希总是指向完全相同的内容，这是“永久Web”的基本理念之一。如果你更改了你的网页，那么你的IPFS新内容将有一个不同的哈希。如果你使用IPNS将你的网页与你的Peer ID绑定，那么你可以对你的网页进行修改并使用IPNS哈希发布你的URL。

## 接下来的步骤

继续下一课，学习如何[修改你的网页并重新发布到IPNS](modify-republish.md)

