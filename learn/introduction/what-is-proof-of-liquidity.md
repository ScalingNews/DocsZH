# 什么是流动性证明

流动性证明 (PoL) 是一种新颖的共识机制，通过增加链上流动性来调节和提高区块链的安全性。

PoL借鉴了权益证明（Proof-of-Stake，PoS）概念，通过提供原生代币（交易手续费使用的gas代币）作为初始质押来保护链的安全。PoL在PoS的基础上进行了扩展，引入了一种额外的不可转让的灵魂绑定治理代币（soulbound governance token）。该代币不仅通过权益委托来决定质押者的潜在奖励权重，还会通过治理奖励金库奖励那些为区块链提供流动性的用户。

<figure><img src="../../.gitbook/assets/流动性证明 (PoL) 流程.png" alt="" width="563"><figcaption></figcaption></figure>

这种模式将用于交易费用的gas代币和用于区块链安全治理的代币的功能分离了。

对应到Berachain，用于交易费用的原生gas代币是[`$BERA`](../proof-of-liquidity/tokens/bera.md)，用于区块链安全治理且不可转让的链上治理代币是[`$BGT`](../proof-of-liquidity/tokens/bgt.md) 。

| 奖励模块     | PoS / Ethereum | PoL / Berachain |
| -------- | -------------- | --------------- |
| 质押 / 安全性 | $ETH           | $BERA           |
| 验证者权重奖励  | $ETH           | $BGT (委托)       |
| 区块奖励     | $ETH           | $BGT (同时重新分配)   |

你可以在[流动性证明概述](../proof-of-liquidity/overview.md)中阅读更多内容。
