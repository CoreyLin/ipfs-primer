# 课程:在IPFS中使用加密哈希来连接片段(一个Merkle DAG)构建一颗数据树

## 课程:从零开始创建一颗Merkle树

### 目标

* 在IPFS中使用密码哈希来连接数据块构建一颗数据树(Merkle DAG)

### 解释: 块 vs 对象

在ipfs中，一个块指的是单个数据单元，由其键(哈希)标识。一个块可以是任何类型的数据，并不一定具有与之关联的任何类型的格式。另一方面，一个对象指的是遵循merkledag protobuf数据格式的一个块。可以通过ipfs object命令对其进行解析和操作。任何给定的哈希都可以表示一个对象或一个块。

## 步骤

### 步骤1

创建你自己的块很容易!简单地把你的数据放在一个文件，然后对它运行`ipfs block put <yourfile>`，或者你可以将文件数据传输到`ipfs block put`中，就像这样

### 步骤2

```text
$ echo "This is some data" | ipfs block put
QmfQ5QAjvg4GtA3wg3adpnDJug8ktA1BxurVqBD8rtgVjM
$ ipfs block get QmfQ5QAjvg4GtA3wg3adpnDJug8ktA1BxurVqBD8rtgVjM
This is some data
```

注意:在生成你自己的块数据时，你无法使用`ipfs cat`读取数据，这是因为你输入的原始数据没有使用unixfs数据格式。要读取原始块，请使用如示例所示的`ipfs block get`。

