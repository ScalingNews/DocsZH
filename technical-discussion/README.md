# 技术讨论

技术讨论分为以下几个主要方面：

* [相关概念](concepts/)：回顾计算机科学中的几个关键概念。
* [为什么选择区块链](why-blockchain.md)？：为去中心化共享全局状态的价值提供心智模型。
* [为什么选择 Monad：去中心化 + 性能](why-monad-decentralization-+-performance.md)：总结了在以太坊中维护共享全局状态的一些现有瓶颈，以及 Monad 如何解决这些瓶颈。
* [共识机制](consensus/)：总结 Monad 的 mempool 和共识层的新颖之处。
* [执行机制](execution/)：概述 Monad 如何执行交易以及如何存储状态。
* [交易生命周期](transaction-lifecycle-in-monad.md)：Monad 交易生命周期的解析。

Monad 在以下四个主要领域实现了流水线作业和优化，以实现卓越的以太坊虚拟机性能，并实质性推动了区块链去中心化和扩容间博弈的有效边界。如果您想专注于这些领域，请参阅以下相关页面：

* [MonadBFT 共识机制](consensus/monadbft.md)（pipelined HotStuff 共识机制，以及更多的研究改进）
* [Deferred Execution / 延迟执行](consensus/deferred-execution.md)（在达成共识和执行之间进行 pipelining 作业，以大幅增加执行预算）
* [Parallel Execution / 并行执行](execution/parallel-execution.md)
* [MonadDb 数据库](execution/monaddb.md)（高性能状态后端）
