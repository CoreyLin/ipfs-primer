# 课程:密码哈希

## 目标

* 了解密码哈希，它们的历史和特征

## 密码哈希的特征

密码哈希被视为字母和数字数据的长字符串。它们是通过将数据作为输入显示给一个 _密码哈希函数_ 来创建的，该函数处理数据并写出一个哈希值或校验和(checksum)。输入数据的长度可以是任意的，但输出哈希的长度总是固定的。

密码哈希有一些非常重要的特征:

* **确定性的** - 相同的输入消息总是返回完全相同的输出哈希
* **不相关的** - 消息中的一个小变化应该会生成一个完全不同的哈希
* **唯一性** - 不可能从两个不同的消息生成相同的哈希
* **单向的** - 不可能从其哈希猜测或计算输入消息

让我们来看看这些特征:

**确定性的:** 只要使用相同的密码哈希函数，就总是会对相同的输入数据得到完全相同的输出哈希值。例如，这允许你验证一个文件中可能有的数据的真实性。如果两个文件在使用相同的密码哈希函数处理时具有相同的输出哈希，那么可以认为数据是相同的。

**不相关的:** 对输入数据的一个小更改应该生成一个完全不同的哈希。这样，这两个哈希值看起来就不相关了。你可以在命令行上演示这一点

```bash
$ echo "Abracadabra!" | ipfs add
added QmWyVG3yhEu8o6EMbUTxcFdzSkddN2NobJye1LhuNajaxy
$ echo "abracadabra!" | ipfs add
added QmdFyNVLCtWxyJDr9osNWMoY6CrnDQQRT8Ypa6MBpkjap3
```

请注意上面两个哈希的巨大差异。通过将第一个字符'A'更改为小写'a'，哈希函数生成了非常不同的输出。

**唯一性:** 不可能从两个不同的消息生成相同的哈希。这是一个构建良好、健壮的密码哈希函数的特征。有些哈希函数可能对不同的消息派生出相同的哈希，这称为 _哈希碰撞_ 。哈希函数随着时间的推移而不断进化，这主要是由于发现了漏洞和弱点。现代密码哈希函数以 _抗碰撞能力强_ 而闻名。由于哈希函数被认为是现代密码学的关键构件，因此在攻击密码哈希函数方面已经做了大量工作。

**单向的:** 不可能从其哈希猜测或计算输入消息。换句话说，你不能反向或反转哈希函数来获得计算它的原始消息。因此，一个密码哈希函数被认为是一个单向函数。有时使用蛮力攻击方法来尝试查找与给定哈希匹配的消息。使用彩虹表(从已知输入的预计算值)是另一种常见攻击。

## History of cryptographic hashes

**MD5:** Designed by Ron Rivest in 1991 to replace an earlier hash function MD4. "MD" stands for "Message Digest". Produces a hash of 128 bits \(16 bytes\). Suitable for non-cryptographic uses, such as basic data integrity. Collisions against MD5 can be calculated within seconds which makes the algorithm unsuitable as a cryptographic hash.

**SHA-1:** Developed as part of the U.S. Government's Capstone project. The original specification of the algorithm was published in 1993. "SHA" stands for "Secure Hash Algorithm". Produces a hash of 160 bits \(20 bytes\). Collisions against SHA-1 have been produced and this hash function should be considered broken.

**SHA-2:** Designed by the United States National Security Agency \(NSA\), first published in 2001. SHA-2 basically consists of two hash algorithms: SHA-256 and SHA-512. SHA-512 is more secure than SHA-256. There are a number of variants of both algorithms. SHA-256 produces a hash of 256 bits \(32 bytes\) and SHA-512 produces a hash of 512 bits \(64 bytes\).

**SHA-3:** Released by NIST in 2015. SHA-3 is a subset of the broader cryptographic primitive family Keccak. SHA-3 has the same output sizes as SHA-2: 224, 256, 384 and 512 bits.

[Read more on Cryptographic Hash Functions](https://en.wikipedia.org/wiki/Cryptographic_hash_function)

## Next Steps

Next, learn how to [Build a Tree of Data in IPFS Using Cryptographic Hashes to Link the Pieces \(a Merkle DAG\)](blocks-from-scratch.md)

