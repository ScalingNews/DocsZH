---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 什么是 Berachain

Berachain是一个具有[EVM等效性](https://www.datawallet.com/zh/%E9%9A%90%E8%94%BD%E6%80%A7/evm-equivalence-explained)的高性能Layer 1区块链，利用[流动性证明 (PoL)](what-is-proof-of-liquidity.md)作为共识机制，建立在面向EVM的模块化共识客户端框架[BeaconKit](what-is-beaconkit.md)之上。

### EVM等效性

Berachain的执行层与以太坊虚拟机（EVM）运行环境相同。这意味着它可以使用现有的[执行客户端](https://ethereum.org/zh/developers/docs/nodes-and-clients/#execution-clients)（如 Geth、Reth、Erigon、Nethermind等）来处理智能合约的执行，而无需修改和重新开发，并支持所有 EVM 原生工具。

这同样意味着无论何时升级EVM，Berachain都可以直接采用最新版本，例如对Dencun的开箱即用。并且包括与所有RPC命名空间和端点兼容，任何来自EVM执行客户端的改进都会在Berachain上同步。

### 流动性证明 <a href="#proof-of-liquidity" id="proof-of-liquidity"></a>

流动性证明是一种共识机制，它建立了一个生态流动性的奖励框架，有助于提高交易效率、稳定价格、保障区块链安全，并促进区块链网络/用户增长。

该框架旨在协调关键利益相关者/[PoL 参与者](../proof-of-liquidity/participants.md)验证者、链上协议、用户）的激励措施，助力区块链总体长期健康发展。

流动性证明为用户提供了出色的Berachain dApps初体验，其中，原生dApps (如[BEX](../native-dapps/bex.md)、[Bend](../native-dapps/bend.md)和[Berps](../native-dapps/berps.md)) 还可以为开发者在流动性证明之上构建dApps提供参考。

你可以在[什么是流动性证明](what-is-proof-of-liquidity.md)中阅读更多内容。

### BeaconKit

BeaconKit是Berachain开发的用于构建EVM共识客户端的模块化框架。它整合了[CometBFT](https://cometbft.com/)共识的优点，包括更全面的可组合性、[单时隙最终性](https://ethereum.org/zh/roadmap/single-slot-finality/#what-is-finality) (SSF) 等。

你可以在[什么是 BeaconKit](what-is-beaconkit.md)中阅读更多内容。
