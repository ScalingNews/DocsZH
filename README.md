# 介绍 Monad

Monad 是与以太坊兼容的高性能 Layer1，Monad 实质性推动了区块链去中心化和扩容间博弈的有效边界。

Monad 在以下四个方面进行了优化，使区块链的吞吐量达到每秒 10,000 笔交易（tps）：

* [MonadBFT 共识机制](technical-discussion/consensus/monadbft.md)
* [延迟执行（Deferred Execution）](technical-discussion/consensus/deferred-execution.md)
* [并行执行（Parallel Execution）](technical-discussion/execution/parallel-execution.md)
* [MonadDb 数据库](technical-discussion/execution/monaddb.md)

Monad 的优化解决了现有区块链的瓶颈问题，同时为应用程序开发人员（完全兼容 EVM 字节码）和用户（兼容以太坊 RPC API）保留了完全兼容性。因此，丰富的以太坊工具和应用密码学研究可以无缝接入到 Monad，同时受益于 Monad 的高吞吐量和交易规模：

* 应用程序（在以太坊上构建的任何 Dapp）
* 开发人员工具（如：Hardhat、Apeworx、Foundry）
* 钱包（如：MetaMask）
* 链上分析/索引工具（如：Etherscan、Dune）

Monad 客户端以性能为核心，采用 C++ 和 Rust 语言编写。下文将介绍 Monad 的主要优化及用户交互。
