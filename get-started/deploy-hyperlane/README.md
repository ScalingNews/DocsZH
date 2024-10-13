---
description: 如何将您的区块链与 Hyperlane 连接
---

# 连接你的链

{% hint style="info" %}
信息

本指南将帮助您尽快地将 Hyperlane 部署到新链上，用于测试而非正式使用。其中包括核心 mailbox 和 ISM 合约，以及用于桥接资产的 warp route 合约。

要查看哪些链受支持，请访问[注册表](../../reference/registries.md)。

如果您需要任何帮助，请在 [Discord](https://discord.com/invite/hyperlane) 的 #developers 频道联系我们。
{% endhint %}

## 前提条件

任何人只要拥有以下工具和资产，就可以开始学习本快速入门指南：

* 选择一个新的、自定义的或已存在的区块链网络，包括以下元数据：
  * 链名，例如 `以太坊`
  * 链 ID，例如 `1`
  * 链 RPC，例如 [`https://eth.llamarpc.com`](https://eth.llamarpc.com)
* 部署者钱包 / EOA 钱包私钥或助记词
  * 该 EOA 钱包应该由您的自定义链以及您将向其传递消息的任何链提供资金
* [Hyperlane CLI](../../reference/cli.md)

## 第一步：注册新链

让我们创建一个自定义链配置，并运行：

```
hyperlane registry init
```

按照提示设置您的链元数据，设置区块或 Gas 属性为自定义。

现在，在 `$HOME/.hyperlane/chains` 下，您可以找到一个以您的自定义链名称命名的新文件夹，该文件夹中有一个名为 `metadata.yaml` 的文件。

<details>

<summary>此配置的示例内容位于 <code>$HOME/.hyperlane/chains/yourchain/metadata.yaml</code></summary>

```
 # yaml-language-server: $schema=../schema.json
 blockExplorers:
   - apiUrl: https://explorer.yourchain.com/api
     apiKey: XXXX # helpful to avoid rate limiting on the contract verification API
     family: etherscan #explorer you're using, also supporting routescan or blockscout
     name: Chainscan
     url: https://explorer.yourchain.com
 chainId: 171717
 displayName: Chain Name
 domainId: 171717
 isTestnet: true # optional
 name: yourchain
 nativeToken:
   name: Ether
   symbol: ETH
   decimals: 18
 protocol: ethereum
 rpcUrls:
   - http: https://hyper-lane-docs.rpc.caldera.xyz/http
```

</details>

## 第二步：部署核心合约

接下来，让我们配置、部署和测试自定义链的核心合约。

#### 初始化 <a href="#initialize-configuration" id="initialize-configuration"></a>

1. 在本地环境中，将部署者地址的私钥或助记词设置为 `HYP_KEY` ，例如： `export HYP_KEY='<YOUR_PRIVATE_KEY>'`
2. 运行相同的 terminal 实例

```
hyperlane core init
```

<details>

<summary>部署配置将写入 <code>./configs/core-config.yaml</code></summary>

```
owner: "0x16F4898F47c085C41d7Cc6b1dc72B91EA617dcBb"
defaultIsm:
  type: trustedRelayerIsm
  relayer: "0x16F4898F47c085C41d7Cc6b1dc72B91EA617dcBb"
defaultHook:
  type: merkleTreeHook
requiredHook:
  owner: "0x16F4898F47c085C41d7Cc6b1dc72B91EA617dcBb"
  type: protocolFee
  beneficiary: "0x16F4898F47c085C41d7Cc6b1dc72B91EA617dcBb"
  maxProtocolFee: "100000000000000000"
  protocolFee: "0"
```

</details>
