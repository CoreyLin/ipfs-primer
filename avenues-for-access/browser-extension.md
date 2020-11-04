# 课程:通过浏览器扩展访问IPFS内容

_这是一个占位符。目前有四种web浏览器扩展可以帮助你从IPFS检索内容。它们的工作方式略有不同。在鼓励人们依赖它之前，我们正在巩固代码并使其更安全。_

当IPFS浏览器扩展完成后，我们将在所有支持它的浏览器的应用程序商店中发布它。当你下载浏览器扩展时，它将自动识别IPFS链接，并使用IPFS点对点网络为你检索内容 -- 不需要HTTP网关，不需要在你的计算机上安装其他东西，不需要使用命令行。你只需安装浏览器扩展，整个IPFS网络就对你可用了。

我们认为这是web浏览器原生支持IPFS的下一个重要步骤。你可以通过[https://github.com/ipfs/in-web-browsers](https://github.com/ipfs/in-web-browsers)在github仓库中跟踪这项工作。[这篇关于一个github issue的评论](https://github.com/ipfs/pm/issues/351#issuecomment-294262546)描述了截至2017年4月这些工作的状态。

除此之外，浏览器中对IPFS的支持将使开始使用真正以内容寻址的链接成为可能，而不需要引用任何HTTP位置，甚至当你通过web浏览器访问内容时也是如此。我们提倡使用一个新的`dweb:` address scheme来实现这一点。使用`dweb:` scheme，我们在本教程的所有课程中使用的[关于访问和分发IPFS内容的各种方法](./)的wikipedia页面链接将是这样的:

* 2017-04-30 snapshot: dweb:/ipfs/Qme2sLfe9ZMdiuWsEtajWMDzx6B7VbjzpSC2VWhtB6GoB1/wiki/Anasayfa.html
* latest \(IPNS\): dweb:/ipns/QmQP99yW82xNKPxXLroxj1rMYMGF6Grwjj2o4svsdmGh7S/wiki/Anasayfa.html
* latest \(DNS\): dweb:/ipns/wikipedia-on-ipfs.io

## 接下来的步骤

返回[关于访问和分发IPFS内容的各种方法的教程](./)，了解使用IPFS使用相同内容寻址的链接访问相同内容的许多其他方法。

