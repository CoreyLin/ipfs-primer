# 修改你的网页并重新发布到IPNS

本课将向你展示如何修改之前添加到IPFS中的简单网页，以及如何将该网页重新发布到IPNS中。

## 目标

学习完这节课，你就能

* 修改你在IPFS中的任何网页并将你的新网页重新发布到IPNS中。

## 步骤

### 步骤1:修改你现有的网页

你将再次工作在`simple-webpage`目录:

```bash
$ cd ~ (or cd %userprofile% on Windows)
$ cd simple-webpage/
```

使用文本编辑器，在`simple-webpage`目录中打开`index.html`文件，并复制/替换下列文本

```bash
<!DOCTYPE html>
<html>
<head>
  <title>Nice Kitty Update</title>
</head>
<body>
  <center>
  <h1>Nice Kitty Update</h1>
  <h2>This is the updated version of our Nice Kitty webpage.</h2>
  <img src="cat.jpg">
  </center>
</body>
</html>
```

在`simple-webpage`目录中保存`index.html`并关闭文本编辑器。

在`simple-webpage`目录中增加一个HTML文件，增加了另一层复杂性。使用文本编辑器，复制/粘贴以下文本:

```bash
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>SECRET</title>
</head>
<body>
This is our SECRET html file, no one will<br>
ever know that we have hidden this here!
</body>
</html>
```

在`simple-webpage`目录中将其保存为`secret.html`，然后关闭文本编辑器。

### 步骤2:将你更新后的网页添加到IPFS中

运行以下命令可将网页更新到IPFS:

```bash
$ cd ..
$ ipfs add -r simple-webpage/
```

你应该看到如下所示的输出

```bash
added Qmd286K6pohQcTKYqnS1YhWrCiS4gz7Xi34sdwMe9USZ7u simple-webpage/cat.jpg
added QmWRijdpZxJVhbUdEmvt2xD4GdCns3EVmTLBRXrJusNmGf simple-webpage/index.html
added QmPx2wNJK3tT5AMPuZwjNAMUkVyR1UB8UYAxx4QmLZovtx simple-webpage/secret.html
added QmXw1gREZvLbNtpEfSCA6cP8SgwhMkbPJrkC93A97uXHqf simple-webpage
 433.27 KiB / 433.27 KiB [=============================================] 100.00%
```

因为`simple-webpage`目录中的内容已经更改，所以该目录的最终哈希现在是不同的。你可能会注意到`cat.jpg`的哈希没有更改，因为没有对该文件进行任何更改。

最后一行的IPFS哈希是用于查看网页的哈希。注意，你自己的哈希可能不同。使用你的IPFS哈希并在浏览器中打开你的网页，如下所示:

`https://ipfs.io/ipfs/your-webpage-hash`

你应该看到“漂亮猫咪更新”的网页。请尝试访问`secret.html`网页:

`https://ipfs.io/ipfs/your-webpage-hash/secret.html`

现在你可以重新发布你更新的网页到IPNS:

```bash
$ ipfs name publish your-webpage-hash
```

你应该看到如下所示的输出

```bash
Published to QmRX....xQTp: (your peer id)
/ipfs/QmZh....your-webpage-hash....9sjT
```

所以你可以看到，当你将更新后的IPFS网页重新发布到IPNS时，它将再次将你的Peer ID绑定到你的更新。这就是能够使用IPNS指向你更新的网页的力量。

使用IPNS链接，以你的Peer ID浏览更新后的网页:

`https://ipfs.io/ipns/your-peer-id`

浏览`secret.html`网页:

`https://ipfs.io/ipns/your-peer-id/secret.html`

## 解释

每次更新网页时，网页的IPFS哈希都会发生变化。通过使用`ipfs name publish`可以使用IPNS重新发布网页,这将每次都使用相同的哈希,绑定到你的Peer ID。这样你可以用你的Peer ID分发你的IPFS link,并且任何使用这个链接访问你的网页的人会在你再次发布后获取最新版本。

## 接下来的步骤

继续下一课，学习如何[生成和使用一个新的IPNS名称Keypair](generate-keypair.md)

