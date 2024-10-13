# 什么是 BeaconKit

BeaconKit是一个模块化、可定制的共识层，适用于基于以太坊开发的区块链，查看 [BeaconKit GitHub 储存库](https://github.com/berachain/beacon-kit)。

BeaconKit是一个创新框架，它使[CometBFT](https://docs.cometbft.com/v0.38/)共识算法适用于任何EVM执行环境。换句话说，BeaconKit是一个模块化的共识层，适用于基于以太坊开发的区块链。

通过利用Engine API接口，BeaconKit可以与任何EVM执行客户端适配，使其与EVM完全等效，无需修改即可完全支持任何EVM执行客户端。

该框架在构建时考虑了模块化，可以轻松整合不同的分层架构，包括自定义区块构建器、汇总层、数据可用性层等。这种模块化框架不仅能够构建Layer 1区块链，还可以作为Layer 2解决方案的框架。

### BeaconKit优势[​](https://docs.berachain.com/learn/what-is-beaconkit#beaconkit-advantages)

* 具有[单时隙确定性](https://ethereum.org/zh/roadmap/single-slot-finality/)（以太坊最终确定约13分钟）。
* 采用Optimistic payload构建（在投票的同时执行区块提案），可将区块时间缩短40%。
* 符合`以太坊 2.0`的模块化需求。
* 完全兼容[以太坊改进提案](https://ethereum.org/zh/eips/)。\
