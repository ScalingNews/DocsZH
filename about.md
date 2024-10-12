---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
---

# 关于 DocsZH

2024年9月29日，币安 (全球最大的加密货币交易所) 创始人，前华人首富[CZ](https://x.com/cz\_binance)出狱，此前CZ因洗钱罪被美国联邦法院判处4个月监禁。出狱后，在迪拜的家中，CZ发布了一条[推特](https://x.com/cz\_binance/status/1839861237850497271)，以告诉人们他重获自由。

### 一条推文引发的讨论

#### 从CZ刑满释放的第一条推文说起...

<figure><img src=".gitbook/assets/20241012161710.png" alt="" width="563"><figcaption></figcaption></figure>

遗憾的是，作为一个中文流利的华人首富，CZ出狱后的第一条推文并没有使用母语，而是发送了两个英文字母：`gm`。

#### `gm`的中文意思是什么？通用汽车？

什么鬼！CZ加入了通用汽车？CZ要向Musk (特斯拉创始人) 发出挑战？CZ要颠覆新能源汽车制造业？那是不是可以叫小鹏汽车，大鹏汽车，敞篷汽车...不对，长鹏汽车！

#### 真相只有一个

上面图片里的翻译结果，由微软翻译自动提供，它错误地将`gm`识别为通用汽车的缩写 (英语：General Motors，缩写为GM）。然而，喜欢在项目方discord里冲浪的Web3黑奴都知道，`gm`的习惯用法，在中文里是`早安`的意思，即`good morning`的首字母缩写。与之用法相似的，晚安`good morning`可以缩写为`gn`。

#### 从Web3黑奴专用语`gm`说起...

当你立志要成为一名Web3黑奴的时候，深夜12点，打开某项目方的协议交互网站。由于不知从何下手，你找到了该项目的使用文档，例如：https://docs.ebeggar.com，映入眼帘的是满屏英文，黑夜给了你黑色的眼睛，你却用它寻找中文。此时，你的浏览器可能会提醒里，要不要将网页翻译为中文。

<figure><img src=".gitbook/assets/20241012165707.png" alt="" width="329"><figcaption></figcaption></figure>

恭喜，黑夜给了你黑色的眼睛，你用它寻找到了中文。加下来，我们会用一个示例，阐述浏览器的自动翻译有多糟糕。

#### 浏览器自动翻译有多糟糕

这里，以我们最近翻译的来自[aPriori](https://beta.rootdata.com/zh/Projects/detail/aPriori?k=OTUwMg%3D%3D)项目的技术博客为例，此处为以下段落的原文链接：[段落原文](https://0xapr.substack.com/p/unlocking-monads-potential-the-critical?open=false#%C2%A7one-block-producer-per-slot-block-space-auction)

**英文原文：**

<figure><img src=".gitbook/assets/20241012171157.png" alt="" width="563"><figcaption></figcaption></figure>

**中文译文：**

<figure><img src=".gitbook/assets/20241012171207.png" alt="" width="563"><figcaption></figcaption></figure>

在谷歌自动翻译的结果中，任何人都能观察到显而易见的错误，例如：

* `One Block Producer per Slot ＞ 每个区块生产者一个区块`**：**语义不通，这是一个病句。

在谷歌自动翻译的结果中，总会有一般人无法理解的内容，例如：

* `slot ＞ 时隙`**：**时隙是什么意思？

在谷歌自动翻译的结果中，总会有专业术语被错误翻译，但一般人无法察觉，例如：

* `inclusion ＞ 包含`**：**在区块链术语中，`包含`翻译为 `(区块) 打包`，更符合技术语境。

### DocsZH 存在的意思和价值

#### 我们尝试优化自动翻译结果

在上述博客节选中，我们处理了错误的病句，对专业术语附注了名词解释，并对语义错误的单词译文进行了符合技术语境的演化。以下是我们的最终译文：

> #### 每个时隙 (Slot) 对应一个区块生产者 ⇒ 区块空间拍卖 <a href="#mei-ge-slot-dui-ying-yi-ge-qu-kuai-sheng-chan-zhe-qu-kuai-kong-jian-pai-mai" id="mei-ge-slot-dui-ying-yi-ge-qu-kuai-sheng-chan-zhe-qu-kuai-kong-jian-pai-mai"></a>
>
> 我们假设，对于任何给定的 [Slot](https://ethereum.org/zh/glossary/#slot)，都有一个区块生产者，对区块排序拥有垄断权力，该区块生产者唯一决定交易的打包和排序，我们将在未来的博文中探讨多个并发领导人设置 ([Solana. 2024](https://docs.google.com/document/d/1zSkhW\_Urp2RbTp\_hKGCefc8o895eCczm5fS1RqzTVVE/edit#heading=h.73njnkwdob7a)) 中的拍卖。鉴于每个 Slot 的区块空间有限，区块生产者必须分配这种稀缺资源，每次对区块排序时，都必须有效地进行区块空间拍卖。

#### 优化自动翻译中出现的病句

在谷歌自动译文中，将`One Block Producer per Slot`翻译为`每个区块生产者一个区块`，造成这种错误的原因是谷歌翻译无法理解区块链的技术原语。以[以太坊](https://ethereum.org/zh/learn/)为例，[时隙](https://ethereum.org/zh/glossary/#slot) (Slot) 是一种时间单位，用于确定网络中[区块提议](https://ethereum.org/zh/developers/docs/consensus-mechanisms/pos/block-proposal/)的频率，设计目的是让[验证者](https://ethereum.org/zh/glossary/#validator)有机会提议新区块。在以太坊中，每12秒为一个时隙，验证者可以在每个时隙中提议区块。

在翻译之前，我们已经对技术原语有足够了解，对于`One Block Producer per Slot`，我们知道作者想说明的是：在排除空时隙的情况下，每个时隙都会有一个验证者提议、打包区块。因此可以将其翻译为：`每个时隙 (Slot) 对应一个区块生产者`。

#### 对专业术语附注解释

在上述博客节选的翻译中，我们保留了`时隙`的对应英文单词`Slot`，并为其添加了名词解释超链接。读者可以通过链接阅读以太坊基金会的中文文档，详细了解`时隙`的名词解释及技术原语。这么做的好处，读者会对`Slot`的名词概念和相关技术原语保留印象，再次看到涉及该名词的内容，阅读会轻松得多。
