# Berachain 测试网 V1 与 V2&#x20;

2024年6月9日，Berachain正式发布了名为`bArtio`的测试网V2版本。

Berachain `bArtio`网络是对区块链的重新架构，使其更加模块化并与EVM兼容。为了实现这些目标，需要一个全新的框架，[BeaconKit](../introduction/what-is-beaconkit.md)应运而生。

V2版本是`BeaconKit`框架的初次实现，它将执行和共识分离，并专注于成为可与任何EVM执行客户端（例如Geth、Reth等）适配的共识客户端。

### 从V1到V2的技术改进[​](https://docs.berachain.com/learn/testnet/berachain-testnet-v1-vs-v2#main-changes-from-v1-to-v2-%F0%9F%90%BB)

Berachain的V1测试网（`Artio`）建立在[Polaris](https://github.com/berachain/polaris)之上，它将EVM执行与Cosmos SDK紧密耦合，并引入了一个用于构建高度优化预编译合约的单体框架。

尽管进行了优化，但Cosmos仍无法处理来自Berachain的大量交易活动，同时，预编译和支持分叉EVM执行客户端也带来了兼容性方面的挑战。

<table><thead><tr><th width="182">技术模块</th><th>Polaris (V1 Artio)</th><th>BeaconKit (V2 bArtio)</th></tr></thead><tbody><tr><td>执行客户端</td><td>EVM (基于Cosmos的预编译分叉)</td><td>EVM (Geth, Reth, Erigon, ...)</td></tr><tr><td>共识算法</td><td>CometBFT</td><td>CometBFT</td></tr><tr><td>最终确定性</td><td>单时隙确定性</td><td>单时隙确定性</td></tr><tr><td>架构类型</td><td>单体式</td><td>模块化</td></tr></tbody></table>

V2引入了将共识层和执行层分分离的模块化架构。V1的验证者只需运行单一的[Polaris](https://github.com/berachain/polaris)客户端，V2验证者需要运行两个客户端，即BeaconKit客户端（用于达成共识）和任一EVM执行客户端（如 Geth、Erigon）。这种模块化架构更加专注于技术专业化：执行层可从EVM的迭代创新中获益，而BeaconKit则提供高度可定制且性能优越的共识层。

### 从V1到V2的代币经济改进

除了BeaconKit的技术改进外，Berachain的原生代币的经济学设计也发生了变化，下表重点介绍了V1和V2之间的主要改进：

| 改进模块         | V1 版本           | V2 版本                           |
| ------------ | --------------- | ------------------------------- |
| 验证者 Bond     | BGT （低供应）       | BERA (69,420)                   |
| 罚没机制         | BGT治理代表（按比例）    | 仅验证者（激活BERA）                    |
| Weighting 奖励 | 委托的BGT          | 委托的BGT                          |
| 出块奖励         | BGT委托权重 = 区块产出率 | 所有验证者 = 区块产出率平均 + BGT委托权重 = 发行量 |
| 架构类型         | Polaris         | Beaconkit                       |
| 验证者数量        | 100             | 128（可能更多）                       |

### 值得注意的要点

* `$BERA`用于激励验证者，而不是`$BGT` 。&#x20;
* `$BGT`代表不再有被罚没的风险。&#x20;
* 现在，执行层与EVM等效。
