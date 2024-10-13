# 建议资源

Monad 与 EVM 字节码完全兼容，支持[上海升级](https://www.evm.codes/?fork=shanghai)后的所有操作码和预编译，Monad 还保留了标准的以太坊 JSON-RPC 接口。

因此，以太坊主网的大部分开发资源都适用于 Monad，本章节为在以太坊上构建去中心化应用程序的开发者提供了一套最基础的资源。

由于 [Solidity](https://docs.soliditylang.org/en/v0.8.25/) 是以太坊智能合约最常用的语言，因此本章节的资源主要集中在 Solidity，包括部分 [Vyper](other-languages/vyper.md) 和[Huff](other-languages/huff.md) 的资源。请注意，由于智能合约是可组合的，最初用一种语言编写的合约仍可以调用另一种语言的合约。

### **集成开发环境（IDEs）**

* [Remix](https://remix.ethereum.org/#lang=en\&optimize=false\&runs=200\&evmVersion=null) 是一款交互式 Solidity 集成开发环境，它是编码和编译 Solidity 智能合约最简单快捷的方式，无需安装其他工具。
* [VSCode](https://code.visualstudio.com/) + [Solidity extension](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity)

### **Solidity 入门教程**

* [CryptoZombies](https://cryptozombies.io/en/course) 是在 EVM 上构建去中心化应用程序的最佳学习教程。它为任何人提供了资源和课程，适用于从零代码编写经验，到希望探索区块链深度开发的所有人员。
* [Solidity by Example](https://solidity-by-example.org/) 通过简单的开发示例，循序渐进地介绍相关概念，最适合已有其他语言开发基础经验的人员阅读。

### **Solidity 中级教程**

* [Solidity Language](https://docs.soliditylang.org/en/v0.8.21/introduction-to-smart-contracts.html) 围绕 EVM 环境，对智能合约和区块链基础知识进行了详细阐述。除了 Solidity Language 文档外，它还涵盖了在 EVM 上编译代码、部署合约的基础知识，以及提供了在 EVM 上部署合约的相关基本组件。
* [Solidity Patterns](https://github.com/fravoll/solidity-patterns) 提供了代码模板库及其用法说明。
* [Uniswap V2](https://github.com/Uniswap/v2-core) 合约是一个专业而易于理解的智能合约，它提供了一个正在运行中的 Solidity dApp 的全局视图，该合约的演示在[此处](https://ethereum.org/en/developers/tutorials/uniswap-v2-annotated-code/)。
* [Cookbook.dev](https://www.cookbook.dev/search?q=cookbook\&categories=Libraries) 提供了一套交互式合约模板示例，具有实时编译、一键部署和人工智能聊天集成功能，可帮助解决代码问题。
* [OpenZeppelin](https://www.openzeppelin.com/contracts) 为 ERC20、ERC712 和 ERC1155 等常见的以太坊代币部署提供了可定制的合约模板。请注意，它们没有进行 Gas 优化。

### **Solidity 高级教程**

* [Solmate](https://github.com/transmissions11/solmate) 资源库和 [Solady](https://github.com/Vectorized/solady/tree/main) 资源库利用 Solidity 或 Yul 提供 Gas 优化合约。
* [Yul](https://docs.soliditylang.org/en/latest/yul.html) 是 Solidity 的一种中间语言，一般可视为 EVM 的内联汇编。它并不完全是纯粹的汇编语言，它提供控制流结构并抽象出堆栈的内部工作，同时仍向开发人员提供原始内存后台。Yul 主要面向需要接触 EVM 原始内存后台的开发人员，以构建高性能、Gas 优化的 EVM 合约代码。
* [Huff](https://docs.huff.sh/get-started/overview/) 最接近于 EVM 汇编，与 Yul 不同，Huff 不提供控制流结构，也不抽象程序堆栈的内部工作。只有对性能最敏感的应用程序才会使用 Huff，但它是学习 EVM 诠释最底层指令的绝佳教学工具。

### **本地节点**

开发人员通常会发现，运行一个修改了参数的以太坊单节点，对交互测试很有帮助：

* [Anvil](https://github.com/foundry-rs/foundry/tree/master/crates/anvil) 是一个打包在 Foundry 工具包中的本地以太坊节点。
* [Hardhat](https://hardhat.org/hardhat-network/docs/overview) 是一个打包在 Hardhat 工具包中的本地以太坊节点。

如何安装相应工具包，并获得本地节点，下一章节将详细介绍。

### **工具包**

开发人员通常会发现，在一个功能齐全的开发框架内构建自己的程序能提高开发效率。开发框架可以组织外部依赖关系（即软件包管理），组织单元测试和集成测试，定义部署程序（针对本地节点、测试网和主网），记录Gas成本等。

以下是两种最常用的 Solidity 开发工具包：

* [Foundry](https://book.getfoundry.sh/) 是一个用于开发和测试的 Solidity 开发框架，Foundry 可以管理依赖关系、编译项目、运行测试、部署，并允许用户通过命令行或 Solidity 脚本与链进行交互，Foundry 用户通常使用 Solidity 语言编写智能合约和测试。
* [Hardhat](https://hardhat.org/docs) 是一个 Solidity 开发框架，搭配有 JavaScript 测试框架，它具有与 Foundry 类似的功能，在 Foundry 出现之前是 EVM 开发人员的主要工具链。

### **与以太坊 RPC API 交互**

去中心化应用程序的前端通常使用 JavaScript 或 Python 向 RPC 节点提交读取或写入查询，这些代码通常被称为 "客户端"，因为开发人员可以将区块链大致等同于后台服务器。

以下资源库提供了向 RPC 节点提交查询或交易的标准方法：

* Python:
  * [web3.py](https://web3py.readthedocs.io/en/stable/)
* Javascript:
  * [web3.js](https://web3js.readthedocs.io/)
  * [ethers.js](https://docs.ethers.org/) 开发了 [Web3.js](https://web3js.readthedocs.io/en/v1.10.0/getting-started.html) 和 [Web3.py](https://web3py.readthedocs.io/en/stable/quickstart.html)，它们分别是 Java Script 和 Python 资源库，这些开发旨在使开发人员能够更直观地与区块链进行交互。

这里是一个创建去中心化应用程序前端的快速示例：[create-eth-app](https://github.com/WalletConnect/create-eth-app)。

### **测试网**

Monad 测试网将在未来几个月内提供给开发者使用，由于字节码和 RPC 与 EVM 兼容，计划在 Monad 上部署的开发者可以初步使用[以太坊测试网](https://ethereum.org/en/developers/docs/networks/)。

### 更多资源

以下子页面添加了额外资源：

* [EVM behavior](evm-behavior.md)
* [更多 Solidity 资源](solidity-resources.md)
* [链上调试](debugging-on-chain.md)
* [其他编程语言](other-languages/)
  * [Vyper](other-languages/vyper.md)
  * [Huff](other-languages/huff.md)
