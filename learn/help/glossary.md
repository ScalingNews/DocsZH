# 术语表

### BERA代币[​](https://docs.berachain.com/learn/help/glossary#bera-token)

`$BERA`是Berachain生态的原生gas代币[​](https://docs.berachain.com/learn/help/glossary#bera-token)，用于支付交易费用，也是用于保护网络安全的初始验证者权益质押代币。更多信息请参阅[$BERA](../proof-of-liquidity/tokens/bera.md)。

### BGT代币

`$BGT`是Berachain的质押和治理代币，且不可转让，通过参与[流动性证明](glossary.md#liu-dong-xing-zheng-ming)获得，也可以通过烧毁`$BGT`获得`$BERA`。该代币用于创建治理提案和对提案进行投票，还可以将其委托给验证者，增加验证者权重以被选中产出区块。更多信息请参阅[$BGT](../proof-of-liquidity/tokens/bgt.md)。

### BeaconKit[​](https://docs.berachain.com/learn/help/glossary#beaconkit)

BeaconKit是一个模块化和可定制的共识层框架，利用CometBFT共识算法构建，且与基于以太坊构架的区块链兼容。更多信息请参阅[BeaconKit](../introduction/what-is-beaconkit.md)。[​](https://docs.berachain.com/learn/help/glossary#beaconkit)

### Block / 区块[​](https://docs.berachain.com/learn/help/glossary#block)

包含交易列表的数据单元，将交易顺序打包，并添加到区块链。

### Bend[​](https://docs.berachain.com/learn/help/glossary#bend)

Berachain的原生借贷协议，从借贷(Lend)一词演化而来。更多信息请参阅[原生dApps > Bend](glossary.md#bend)。

### BEX[​](https://docs.berachain.com/learn/help/glossary#bex)

Berachain的原生去中心化交易所，从去中心化交易所(DEX_)_一词演化而来。更多信息请参阅[原生dApps > BEX](../native-dapps/bex.md)。

### Berps[​](https://docs.berachain.com/learn/help/glossary#berps)

Berachain的原生永续合约交易所，从永续合约(Perps_)_一词演化而来。更多信息请参阅[原生dApps > Berps](../native-dapps/berps.md)。

### Block Time[​](https://docs.berachain.com/learn/help/glossary#block-time) / 区块时间

区块链上产出新区块所需的时间。Berachain的平均区块时间为：<3秒。请注意，如果网络拥堵，区块时间可能会增加。

### CometBFT[​](https://docs.berachain.com/learn/help/glossary#cometbft)

Berachain正在采用的一种通用区块链共识引擎，用于实现高吞吐量和交易快速确认。更多信息请参阅[Cometbft](https://cometbft.com/)。

### Consensus Client / 共识客户端[​](https://docs.berachain.com/learn/help/glossary#consensus-client)

共识客户端是一款软件，负责在网络节点之间就区块链的当前状态达成一致。它负责处理交易和区块的验证流程，确保它们符合网络规范，并决定将哪些区块添加到区块链中。共识客户端专注于网络全局的规范和交易顺序的监督。它通常与执行客户端协作使用。

### Consensus Mechanism / 共识机制[​](https://docs.berachain.com/learn/help/glossary#consensus-mechanism)

Berachain网络中的节点根据共识机制就区块链的状态达成一致。Berachain的PoL共识机制根据验证者提供的流动性权重来选择验证者。

### Delegation / 委托[​](https://docs.berachain.com/learn/help/glossary#delegation)

代币持有人向网络中的其他参与者授予投票或验证权力的过程。

### DEX / 去中心化交易所[​](https://docs.berachain.com/learn/help/glossary#dex-decentralized-exchange)

一个无需第三方提供交易中介服务，直接在区块链上买卖代币的平台，所有流动性均通过智能合约实现。

### Engine API[​](https://docs.berachain.com/learn/help/glossary#engine-api)

Engine API是一个接口，允许EVM节点的执行层和共识层之间进行通信。[BeaconKit](../introduction/what-is-beaconkit.md)作为共识层，利用Engine API可以实现与任何执行客户端适配。

### Execution Client / 执行客户端[​](https://docs.berachain.com/learn/help/glossary#execution-client)

执行客户端（有时称为执行层）是一个软件应用程序，负责区块内交易的实际计算。EVM执行客户端使用EVM解析和执行智能合约代码，管理状态更改并执行交易逻辑。EVM客户端确保所有操作均根据智能合约的代码和EVM协议正确执行。

以下是常用的EVM执行客户端：

* Geth：由以太坊协议的官方Go语言实现。
* Erigon：从go-ethereum分叉出来的性能更高、功能更丰富的客户端。
* Nethermind：基于.NET框架的客户端，完全支持以太坊协议。
* Besu：企业级客户端，采用Java语言编写，获得Apache 2.0许可。
* Reth：基于Rust语言的客户端，注重性能和可靠性。
* Ethereumjs：以太坊基金会管理的基于Javascript的客户端。

### Finality / 最终确定性[​](https://docs.berachain.com/learn/help/glossary#finality)

确保交易一旦在区块链上确认，就无法篡改或撤销。Berachain为交易提供[单时隙最终性](https://ethereum.org/zh/roadmap/single-slot-finality/#what-is-finality)。

### Governance / 治理[​](https://docs.berachain.com/learn/help/glossary#governance)

Berachain生态的决策管理系统。治理涉及提案、投票和变更的实施，通常使用`$BGT`代币参与治理。

### HONEY[​](https://docs.berachain.com/learn/help/glossary#honey)

`$HONEY`是Berachain生态的原生稳定币，与`$USDC`锚定。它应用于整个Berachain生态，有铸造和销毁费用。更多信息请参阅[原生代币系统>$HONEY](../proof-of-liquidity/tokens/honey.md)。

### IBC[​](https://docs.berachain.com/learn/help/glossary#ibc)

一种跨链通信协议，提供基于Cosmos开发的区块链间的数据传输和互操作性服务。

### Liquidity / 流动性[​](https://docs.berachain.com/learn/help/glossary#liquidity)

体现两种不同加密资产之间稳定兑换的难易程度，流动性通常由用户通过流动性池提供。

### Liquidity Pool / 流动性池[​](https://docs.berachain.com/learn/help/glossary#liquidity-pool)

锁定在智能合约中的资金池，用于为去中心化交易所和其他DeFi服务提供流动性。Berachain上的流动性池可以容纳2种代币。

### Liquidity Provider / 流动性提供者[​](https://docs.berachain.com/learn/help/glossary#liquidity-provider)

将代币资产存入流动性池的用户，可从池中产生的swaps费用中获得部分收益。

### Mainnet / 主网[​](https://docs.berachain.com/learn/help/glossary#mainnet)

在Berachain中，主网指发生真实交易的区块链网络，主网代币资产具有实际价值，与用于提供开发环境的测试网对应。

### Polaris EVM[​](https://docs.berachain.com/learn/help/glossary#polaris-evm)

以太坊虚拟机的整体实现，构建在Cosmos SDK之上。在测试网V1版本中，Berachain采用Polaris以实现与以太坊智能合约的兼容性。在测试网V2版本中，Polaris已被弃用，取而代之的是模块化架构BeaconKit。

### 流动性证明[​](https://docs.berachain.com/learn/help/glossary#proof-of-liquidity)

Berachain所开创的共识机制，验证者具有公平的提议区块的机会，验证者奖励与用户委托给验证者的`$BGT`数量成比例关系。

### Single Slot Finality / 单时隙确定性[​](https://docs.berachain.com/learn/help/glossary#single-slot-finality)

指区块可以在同一Slot内提议并最终确定，无需等待，有时也称为_即时最终性_。

### Staking / 质押[​](https://docs.berachain.com/learn/help/glossary#staking)

锁定代币资产以支持区块链网络运行的过程。在Berachain中，质押用于保护网络安全和参与治理。

### Swap / 兑换[​](https://docs.berachain.com/learn/help/glossary#swap)

Swap是指在去中心化交易所中，将一种代币兑换成另一种代币的过程，可以看作是买入或出售加密资产。例如，如果你想用`$ETH`购买`$BERA`，你需要将`$ETH`swap成`$BERA`，这本质上就是卖出`$ETH`，同时买入`$BERA`。

每次swap都需要支付交易手续费，具体取决于创建池时设定的协议费用，常见的协议费用为0.05%、0.1%、0.3%或1%，用户在swap时应始终检查，以确保对该池的协议费用满意。
