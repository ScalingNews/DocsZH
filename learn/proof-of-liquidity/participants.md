# 流动性证明参与者

下图展示了流动性证明生态系统中不同参与者的角色细分。

<figure><img src="../../.gitbook/assets/val-stakeholder-overview.png" alt="" width="563"><figcaption></figcaption></figure>

### 验证者[​](https://docs.berachain.com/learn/pol/participants#validators-%E2%9C%85)

验证者相互协调，就区块链的状态达成共识。为了获得网络奖励，验证者必须抵押资产，如果行为不当，可能会受到惩罚。要成为主动验证者，必须抵押`$BERA`代币。验证者通过三种主要方式获得收益：

1. Gas费和优先费
2. 将`$BGT`奖励存入协议方，收集协议方提供的激励
3. 从产出区块所获得的`$BGT`总收入中抽取佣金

第1点很简单，与以太坊PoS机制相同。第2点涉及有趣的PoL机制。

#### 验证者激励[​](https://docs.berachain.com/learn/pol/participants#validator-incentives-%F0%9F%92%8E)

正如在[$BGT](tokens/bgt.md)中讨论的那样，每个区块的`$BGT`发行量是根据提议该区块的验证者的`$BGT`委托权重来分配。每个区块的提议验证者有权将区块的`$BGT`奖励分配给他们选择的任何协议金库，并收取协议方提供的相关激励。任何验证者都有提议区块的平等机会。

验证者最初的`$BGT`委托权重为0，此时验证者不会将提议区块奖励的`$BGT`分配给任何协议金库。然而，通过证明他们正在寻找最有利可图的协议金库来分配`$BGT`，并将部分奖励返还给`$BGT`委托人，他们可以吸引到更多的委托。

#### 生态系统协调[​](https://docs.berachain.com/learn/pol/participants#ecosystem-alignment-%E2%9A%96%EF%B8%8F)

流动性证明中的验证者不仅仅是 “验证” 网络，他们还有机会与协议方合作，以繁荣其在Berachain链上的流动性。最终，他们必须赢得用户（即`$BGT`持有者和矿工）的青睐，以便更高效地将更多`$BGT`奖励分配给金库并赚取奖励。

### $BGT持有人和Farmers <a href="#bgt-holders-farmers" id="bgt-holders-farmers"></a>

`$BGT`持有人在以下方面发挥着至关重要的作用：

1. 通过参与治理影响生态系统决策
2. 影响Berachain的经济激励措施的未来方向（通过将`$BGT`委托给验证者）

{% hint style="info" %}
委托给验证者的`$BGT`不会被罚没，只有验证者质押的`$BERA`受罚没机制约束。
{% endhint %}

#### 赚取$BGT[​](https://docs.berachain.com/learn/pol/participants#earning-bgt-%E2%AC%87%EF%B8%8F)

作为寻求赚取`$BGT`的Farmer，考虑到风险和资产敞口状况，要发掘最有利可图的奖励金库来挖矿。这意味着需要从符合标准的验证者里，寻找那些能给予最多`$BGT`奖励的金库。例如，如果你只想接触稳定币，你可以选择通过向[Berps](../native-dapps/berps.md)协议提供`$HONEY`流动性来赚取`$BGT`。

#### 委托$BGT[​](https://docs.berachain.com/learn/pol/participants#delegating-bgt-%E2%AC%86%EF%B8%8F)

现在你是`$BGT`持有者，不同因素可能会影响你如何选择委托方，例如：

* 你可以委托`$BGT`给验证者，他们将`$BGT`奖励分配到你耕种的金库（以增加你的收益率）。
* 你可以委托`$BGT`给验证者，他们将奖励金库激励最大化，并将最大化的收益返还给持有者。

### Bera基金会[​](https://docs.berachain.com/learn/pol/participants#bera-foundation-%F0%9F%8F%9B%EF%B8%8F)

该基金会负责运营原生dApps（Bex、Bend、Berps），这些原生dApps赚取的协议费用将分配给`$BGT`持有者。（这样就有赚取 `$BGT` 的原生方式，独立于奖励金库激励。）

这些dApps的流动性也可作为原生奖励金库，为用户提供流动性并赚取`$BGT`，直到其他协议方的奖励金库通过治理程序与PoL连接。

### 生态协议方[​](https://docs.berachain.com/learn/pol/participants#ecosystem-projects-%F0%9F%A7%B8)

PoL是一种全新的协议启动存款的方式，与通过流动性挖矿激励流动性的传统方法不同。连接PoL，协议可以通过将来自验证者的`$BGT`奖励引导到协议奖励金库来促进流动性。

由于所有奖励都围绕`$BGT`，因此所有链上的参与者都致力于提高网络的总体价值。如果`$BGT`奖励的价值上升，项目代币（作为奖励保存在奖励金库中）的价值也会随着存款的增加而相应增加。

最后，新加入的生态协议项目方必须成为积极参与者，赢得`$BGT`持有者和代表的青睐，才能将其奖励金库列入PoL系统白名单。
