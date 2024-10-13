# 奖励金库白名单

Berachain的流动性证明PoL共识机制允许协议方通过接收来自验证者的`$BGT`来启动协议流动性。此过程由奖励金库实现，奖励金库在Berachain生态的治理和激励中发挥着至关重要的作用。

{% hint style="info" %}
有关如何创建奖励金库的详细指南，请参阅博文：\
[Creating a Governance Proposal for Berachain Reward Vaults](https://blog.berachain.com/blog/creating-a-governance-proposal-for-berachain-reward-vaults)
{% endhint %}

### 了解PoL奖励金库[​](https://docs.berachain.com/learn/governance/rewardvault#understanding-reward-vaults-in-pol)

奖励金库是一种智能合约，使验证者能够与协议分享`$BGT`奖励。当验证者产出区块时，他们获得的`$BGT`奖励与其质押数额成正比。验证者可以：

1. 使用`$BGT`参与治理
2. 将`$BGT`兑换为`$BERA`（原生gas代币）
3. 通过奖励金库与协议分享`$BGT`奖励

该机制是Berachain[奖励金库](../proof-of-liquidity/rewardvaults.md)系统的核心。

### 治理和奖励金库[​](https://docs.berachain.com/learn/governance/rewardvault#governance-and-reward-vaults)

虽创建奖励金库无需许可，但为了接收来自验证者的`$BGT`，金库必须通过治理提案，被列入白名单。此过程确保了社区监督与PoL系统的目标保持一致。

#### 白名单治理流程 <a href="#governance-process-for-whitelisting" id="governance-process-for-whitelisting"></a>

1. **满足`$BGT`持有要求**
   * 创建提案所需的最低`$BGT`数额
   * `$BGT`可通过向原生dApps提供流动性获得
2. **创建并提交提案**
   * 提案在链上提交
   * 投票开始前有一个等待期
3. **提案投票**
   * 开启投票窗口
   * `$BGT`持有人投票（需达到法定数）
4. **提案结果**
   * 如果通过：进入锁定期，待执行
   * 如果未通过：标记为失败，允许在解决相关问题后重新提交

{% hint style="info" %}
测试网提案详细标准（如所需`$BGT`数额、投票期和法定数要求等），请参阅[治理模型概述](overview.md)。
{% endhint %}

<figure><img src="../../.gitbook/assets/governance-process (1).png" alt="" width="563"><figcaption></figcaption></figure>

### 对PoL系统的影响[​](https://docs.berachain.com/learn/governance/rewardvault#impact-on-the-pol-ecosystem)

通过治理将奖励金库列入白名单具有重大意义：

1. **流动性激励**：经批准的金库可以接收`$BGT`奖励，激励用户向其提供流动性。
2. **协议增长**：协议可以使用积累的`$BGT`来吸引流动性或参与治理。
3. **生态系统协调**：白名单治理能确保金库与生态社区利益保持一致。

有关奖励金库的更多信息，请参阅[奖励金库](../proof-of-liquidity/rewardvaults.md)。

有关Berachain治理的更多信息，请参阅[治理模型概述](overview.md)。

有关为Berachain奖励金库创建治理提案的更多信息，请参阅博文：

[Creating a Governance Proposal for Berachain Reward Vaults](https://blog.berachain.com/blog/creating-a-governance-proposal-for-berachain-reward-vaults)
