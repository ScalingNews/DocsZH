# 流动性证明常见问题

#### 没有代币的dApps可以参与PoL吗？[​](https://docs.berachain.com/learn/pol/faqs#can-dapps-that-don-t-have-a-token-still-participate-in-pol)

然也。PoL流动性证明的基础之一是启用白名单奖励金库。协议只需要发行一个凭证代币，该凭证代币可以质押在协议自身的白名单奖励金库。凭证代币与原生代币不同，可以被视为是原生代币的证明。例如，当用户向Bex提供流动性时，他们会收到LP代币形式的凭证代币。

#### 哪些类型的dApps可以拥有白名单奖励金库？[​](https://docs.berachain.com/learn/pol/faqs#are-there-restrictions-on-what-kinds-of-dapps-can-have-whitelisted-reward-vaults)

任何dApps都可以部署奖励金库并将其作为治理提案提交，以将金库列入白名单。

#### Bex流动性池的APY由什么决定？[​](https://docs.berachain.com/learn/pol/faqs#what-determines-the-apy-for-pools-in-bex)

APY奖励由以下方面决定：

1. **流动性池产生的协议费用**：由流动性池中产生的交易和设定的费用系数决定。产生的交易越多，协议费用就越多。费用系数越高，单次交易产生的协议费用越高。但是，协议费用系数应设定在一个合理范围，以确保用户不会因协议费用过高而放弃交易。
2. **流动性池中$BGT分配数额**：这是每个周期中Berachain验证者的投票决定的。每个验证者可以选择他们希望接收其`$BGT`奖励的池，以及每个池应获得的`$BGT`分配数额。验证者`$BGT`奖励是根据所有`$BGT`持有人委托给该验证者的`$BGT`权重确定的。分配给某流动性池的`$BGT`数额越多，则该池的PRR越高。
3. **用户在奖励金库中的质押数额**：分配给流动性池的`$BGT`会按比例派发给所有为该池投入`$BGT`的用户。

#### 奖励金库的**$**BGT奖励是否与该金库的流动性（例如TVL）成比例？[​](https://docs.berachain.com/learn/pol/faqs#is-the-amount-of-bgt-rewarded-to-a-rewards-vault-proportional-at-all-to-the-amount-of-liquidity-e-g-tvl-of-that-rewards-vault)

非也。随着时间推移，可能会出现一定的比例关系，但这不是决定性因素。

#### **$**BGT奖励分配是否与委托给验证者的**$**BGT数量成线性关系？[​](https://docs.berachain.com/learn/pol/faqs#is-the-size-of-the-bgt-emission-linear-to-the-amount-of-bgt-delegated-to-a-validator)

然也。对于无人委托的验证者，有一个基准`$BGT`分配参数，除此之外，`$BGT`分配根据委托的BGT数量呈线性变化。

#### 任何人都可以质押**$**BERA成为验证者吗？[​](https://docs.berachain.com/learn/pol/faqs#can-anyone-stake-bera-to-become-a-validator)

目前，成为验证者需要获得许可，但预计未来会开放。

#### 原生dApps（BEX、Bend Berps）和外部dApp参与PoL是否有区别？[​](https://docs.berachain.com/learn/pol/faqs#is-there-any-difference-between-the-ability-for-native-dapps-bex-bend-berps-and-external-dapps-to-participate-in-pol)

非也。所有奖励金库都必须通过治理批准，才有资格接收BGT奖励分配。例如，并非所有BEX池都能获得`$BGT`奖励（因为它们不在白名单中）。

#### “流动性池”和“奖励金库”有什么区别？[​](https://docs.berachain.com/learn/pol/faqs#what-is-the-difference-between-a-pool-and-a-rewards-vault)

一般来说，流动性池是指Berachain上DeFi协议中的存款，可以是Dex上的LP，借贷协议中的凭证代币。奖励金库（在PoL白名单中）是单独的智能合约，允许用户将这些流动性凭证代币质押以赚取`$BGT`奖励。

#### 奖励金库是否只能通过白名单治理提案创建？[​](https://docs.berachain.com/learn/pol/faqs#are-rewards-vaults-created-only-by-whitelisting-governance-proposals)

从技术上讲，奖励金库的创建无需许可，但验证者要想将`$BGT`存入奖励金库，则该奖励金库必须是已被列入白名单。

#### 能否举例说明$BGT投票权与$BGT分配的关系？[​](https://docs.berachain.com/learn/pol/faqs#can-you-give-me-an-example-of-bgt-voting-power-in-relation-to-bgt-emissions)

验证者的$BGT奖励与其投票权成正比。在Bartio测试网上，每个区块的通膨率固定为1500`$BGT`左右。如果一个拥有25%`$BGT`投票权的验证者产出一个区块，其将获得约375`$BGT`的奖励，并转入奖励金库，这些奖励金库根据收到的`$BGT`数量支付奖励。因此，验证者奖励与其拥有的`$BGT`委托量有关，如果一个拥有10%`$BGT`投票权的验证者产出区块，其只能获得150`$BGT`。

#### 担心$BGT会出现恶性通货膨胀，Berachain计划如何解决这个问题？[​](https://docs.berachain.com/learn/pol/faqs#i-have-concerns-about-hyperinflation-of-bgt-how-does-berachain-manage-this)

传统的PoS系统每年都会有一定比例的通胀，Berachain只是将PoS通胀分成了以下两部分：

1. 仅有`$BERA`质押，未有`$BGT`委托权益的验证者产出区块获得的优先费用。
2. 基于委托给验证者的`$BGT`数量的权益权重系数。

PoS通胀等于以上两条相加，基本上第2条是所有验证者`$BGT`委托的加权平均值，它与平均通胀率吻合。

最终结果是，Berachain通胀与传统PoS相差无几，只是分配方式不同。

#### 如何为LP代币定价，以$BGT的LP为例？为安全起见，Berachain是否会限制$BGT流动性池质量？[​](https://docs.berachain.com/learn/pol/faqs#how-do-you-manage-to-price-the-lp-token-which-in-this-case-bgt-does-berachain-limit-the-number-of-pools-receiving-bgt-to-blue-chips-for-security-right)

`$BGT`没有定价，也不是LP代币，它是一种不可转移的灵魂绑定代币，通过在Berachain上提供DeFi流动性来赚取。在`$BGT`治理白名单中，由市场自由决定`$BGT`流动性池的数量。因此，在同等条件下，绩优的`$BGT`流动性池可能会获得更多的`$BGT`奖励（因为流动性聚集在此），而长尾资产在没有过多激励的情况下获得的`$BGT`较少。

#### 为什么激励措施以每$BGT为单位，而不是以流动性池为单位？[​](https://docs.berachain.com/learn/pol/faqs#why-are-incentives-emission-defined-per-bgt-instead-of-being-pool-based)

激励措施以`$BGT`为单位，因为用户最终希望能够计算出，委托一个`$BGT`和质押一个`$BGT`，两者能获得的奖励差异。因此，这更像是用户体验的不同选择，以方便理解`$BGT`的不同价值驱动。

#### 只有验证者才能投票或创建提案吗？[​](https://docs.berachain.com/learn/pol/faqs#can-only-validators-vote-on-or-create-proposals)

非也。任何拥有一定数量的`$BGT`用户都可以创建提案或投票。

#### 如果验证人想降低权重，验证人质押是否可以提取？验证人是否能够从其初始$BERA质押中获得收益？[​](https://docs.berachain.com/learn/pol/faqs#can-validator-deposits-ever-be-withdrawn-ie-if-someone-wants-to-spin-down-their-validator-do-depositors-earn-yield-tips-on-their-initial-deposit-of-bera)

在启用EIP-7002之前，验证人质押不能提取。请等待下一次硬分叉，这样节省了大量工程时间和代码复杂性。质押只是为了验证人激活，质押本身不会产生收益。

#### 没有$BGT委托的验证者可以产出区块吗？这些验证者在产出区块时会获得什么奖励？[​](https://docs.berachain.com/learn/pol/faqs#can-validators-with-no-bgt-delegated-to-them-build-blocks-what-kind-of-rewards-will-those-validators-earn-when-they-build-a-block)

然也。他们可以产出区块，这些验证者只能获得交易的优先费用，而不会获得任何`$BGT`奖励。

#### 奖励金库是将奖励派发到dApp中的单个池，还是整个dApp？[​](https://docs.berachain.com/learn/pol/faqs#can-rewards-vaults-route-emissions-to-a-single-pool-within-a-dapp-or-only-the-whole-dapp)

dApp可以为任何协议封装资产申请PoL金库白名单，该封装资产只需部署一个ERC-20凭证代币，用户就可以将其质押到金库中。

#### Berachain是否限制了主动验证者的数量（例如256个），如何才能成为主动验证者？[​](https://docs.berachain.com/learn/pol/faqs#do-we-cap-the-number-of-active-validators-e-g-at-256-is-there-a-queue-for-entering-the-active-set)

我们将建立一种机制，将主动验证者的数量限制在一个安全水平。

#### 验证者节点需要持有69420个$BERA才能开启质押，这是准确数字吗？[​](https://docs.berachain.com/learn/pol/faqs#it-claims-that-a-validator-node-needs-69-420-bera-to-stake-is-this-accurate)

69420个`$BERA`只是暂时的占位符设置，我们将在接近主网时确定最终值。

#### 验证者节点有质押数额上限吗？[​](https://docs.berachain.com/learn/pol/faqs#is-there-a-maximum-staking-amount-with-a-validator-node)

没有硬性上限，但多余的`$BERA`质押不会获得额外的提议新区块的权重。

#### 验证者的哪些资产有可能被罚没？[​](https://docs.berachain.com/learn/pol/faqs#what-asset-is-at-risk-to-be-slashed-for-validators)

`$BERA`属于担保资产，有可能被罚没。
