# 常见问题

#### Berachain的性能指标如何？[​](https://docs.berachain.com/learn/help/faqs#what-do-berachain-s-performance-metrics-look-like)

Berachain具有以下属性：

* 区块时间：区块时间各不相同，最新信息请查看[Beratrail区块浏览器](https://bartio.beratrail.io/)。
* 每秒交易笔数（TPS）：可能会有变化，下方公式可用于计算TPS：

$$
TPS=区块gas限制(30m) / 每笔交易平均gas限制 / 区块时间(2s)
$$

* 最终确定性：单时隙确定性。

#### 什么是DEX？[​](https://docs.berachain.com/learn/help/faqs#what-is-a-dex)

DEX全称去中心化交易所，其不由任何中心化服务商运行。用户可以使用钱包连接DEX，直接从钱包买卖、兑换各种链上资产，而无需将资产存入第三方托管账户。这意味着所有资产的流动性都可以直接在链上看到，并且可以验证由智能合约部署，DEX还允许任何人推出自己的代币并提供流动性。

#### 什么是兑换(Swap)？[​](https://docs.berachain.com/learn/help/faqs#what-is-a-swap)

Swap是指将一种代币兑换成另一种代币的过程，可以看作是买入或出售加密资产。例如，如果你想用`$ETH`购买`$BERA`，你需要将`$ETH`swap成`$BERA`，这本质上就是卖出`$ETH`，同时买入`$BERA`。

#### 兑换(swap)需要多少交易手续费？[​](https://docs.berachain.com/learn/help/faqs#how-much-does-it-cost-to-swap)

每次swap都需要支付交易手续费，具体取决于创建池时设定的协议费用，常见的协议费用为0.05%、0.1%、0.3%或1%，用户在swap时应始终检查，以确保对该池的协议费用满意。

#### 什么是流动性(liquidity)？[​](https://docs.berachain.com/learn/help/faqs#what-is-liquidity)

流动性是指可用于swap的代币数量。代币的流动性越高，swap成功率越高。

#### 什么是流动性池(liquidity pool / LP)？[​](https://docs.berachain.com/learn/help/faqs#what-is-a-liquidity-pool)

流动性池是流动性提供者将两种不同代币进行成对存款的地方，从而DEX用户可以在任意两种代币之间进行swap。

#### 什么是流动性提供者？[​](https://docs.berachain.com/learn/help/faqs#what-is-a-liquidity-provider)

流动性提供者是指将代币存入流动性池的用户，流动性提供者可以获得该池一定比例的协议费用奖励。

#### 什么是APY？[​](https://docs.berachain.com/learn/help/faqs#what-is-apy)

APY指年化收益率。在BEX池中，它指的是特定池的当前APY。

#### 什么是$HONEY？[​](https://docs.berachain.com/learn/help/faqs#what-is-honey)

`$HONEY`是Berachain生态系统的原生稳定币。它是一种由`$USDC`支持的稳定币，应用于整个Berachain生态系统。

#### 铸造或销毁$HONEY需要支付手续费吗？[​](https://docs.berachain.com/learn/help/faqs#does-it-cost-anything-to-mint-or-burn-honey)

为了确保稳定性，每次铸造和销毁`$HONEY`时都会收取少量费用。目前，该费用设置为铸造或销毁金额的0.5%，费用设置可通过治理提案进行更改。

此外，由于铸造和销毁需要交易，因此需要小额gas费用`$BERA`。

#### 测试网期间，哪些稳定币可以铸造$HONEY？[​](https://docs.berachain.com/learn/help/faqs#what-stablecoins-can-i-mint-honey-with-during-testnet)

有多种与美元挂钩的稳定币可用于铸造`$HONEY`。目前，测试网支持以下稳定币铸造`$HONEY`，也可能会根据治理情况添加更多代币：

* stgUSDC

#### 什么是$BGT？[​](https://docs.berachain.com/learn/help/faqs#what-is-bgt)

`$BGT`是Berachain的质押和治理代币，用于保障区块链安全，并是流动性证明的奖励代币，还可以在治理提案中拥有投票权。

#### 什么是验证者？[​](https://docs.berachain.com/learn/help/faqs#what-is-a-validator)

验证者包括以下角色：

1. 运行区块链节点以验证交易、生成区块并与网络中的其他验证者达成共识。
2. 拥有并运行验证者节点的实体。
3. 第1点和第2点的结合，管理部分流动性证明和进行治理投票。

[BGT Station](https://bartio.station.berachain.com/)属于上述第3种，BGT Station为用户提供参考，以决定委托给哪些验证者。

#### 为什么要委托$BGT？[​](https://docs.berachain.com/learn/help/faqs#why-should-i-delegate-my-bgt)

委托`$BGT`可以参与流动性证明，同时帮助保护区块链安全。

#### 为什么要委托$BGT而不是将其销毁以获得$BERA？

`$BGT`可以获得额外奖励是主要原因。有了流动性证明机制，`$BGT`持有人可以获得比任何其他链都多的奖励，如下：

* `$BGT` 通胀
* 链上价值捕获
  * DEX协议费用
  * $HONEY协议费用
  * Perps协议费用
* Gas费用

#### 如何获得$BGT？[​](https://docs.berachain.com/learn/help/faqs#how-do-i-get-bgt)

当验证者将`$BGT`存入奖励金库时，用户即可通过流动性证明获得奖励金库的`$BGT`。参阅[`$BGT`](../proof-of-liquidity/tokens/bgt.md)以了解更多信息。

#### 什么是治理？[​](https://docs.berachain.com/learn/help/faqs#what-is-governance)

治理是指社区决定对Berachain生态系统进行改进的过程。包括如何升级节点以及为链上的各个组件设置哪些参数。

#### BEX中的PoL白名单池的流动性提供者如何获得$BGT奖励？$BGT是否自动发送给流动性提供者？[​](https://docs.berachain.com/learn/help/faqs#once-you-ve-provided-liquidity-into-an-eligible-pool-in-bex-or-some-other-bgt-generating-action-like-bend-etc-how-do-you-get-bgt-is-bgt-automatically-sent-to-recipients)

BEX上每个合格的白名单流动性池都有一个关联的LP代币，用户将流动性存入合格的BEX池，协议将根据用户在该池的份额发放LP代币，随后用户必须将该LP代币质押进对应的奖励金库中，才有资格获得`$BGT`奖励。

同时当验证者将`$BGT`分发到奖励金库时，用户便可以申领积累的`$BGT`奖励，用户必须采取额外操作才能申领`$BGT`奖励，奖励不会自动发送给用户。

#### 只有验证者可以投票或创建提案吗？[​](https://docs.berachain.com/learn/help/faqs#can-only-validators-vote-on-or-create-proposals)

非也。任何拥有一定数量的`$BGT`持有人都可以创建提案，以及对提案投票。

#### Berachain中的实际质押代币是$BERA还是$BGT？[​](https://docs.berachain.com/learn/help/faqs#what-is-the-actual-staking-token-of-the-network-bera-or-bgt)

权益质押->`$BERA`，PoL奖励->`$BGT`

#### 仅拥有$BERA的验证者可以产出区块吗？奖励是什么？[​](https://docs.berachain.com/learn/help/faqs#can-validators-with-bera-alone-build-blocks-and-what-are-the-rewards)

然也。此类验证者可以获得交易优先费用，以及发送到其验证者地址的`$BGT`gas基本費用。

#### 只有拥有$BGT委托权益的验证者才能获得奖励吗？[​](https://docs.berachain.com/learn/help/faqs#do-incentives-only-go-to-the-validators-with-bgt-delegated-to-them)

验证者获得的奖励取决于其拥有的`$BGT`委托权重。

#### 奖励金库是将奖励派发到dApp中的单个池，还是整个dApp？[​](https://docs.berachain.com/learn/pol/faqs#can-rewards-vaults-route-emissions-to-a-single-pool-within-a-dapp-or-only-the-whole-dapp)[​](https://docs.berachain.com/learn/help/faqs#can-reward-vaults-route-emissions-to-a-single-pool-within-a-dapp-or-only-the-whole-dapp)

dApp可以为任何协议封装资产申请PoL金库白名单，该封装资产只需部署一个ERC-20凭证代币，用户就可以将其质押到金库中。
