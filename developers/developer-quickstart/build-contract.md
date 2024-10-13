# ERC-20 代币合约部署

[ERC-20代币标准](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)为Berachain网络代币部署提供了通用接口。ERC-20遵循标准接口，因此其他应用程序可以轻松地在链上与它们交互，并且可以扩展更多功能。该标准为用户提供从简单代币转移到复杂DeFi交互的全方位支持。

本节中，我们将介绍如何使用Solidity创建ERC-20代币，并将其部署到Berachain测试网。

### 先决条件[​](https://docs.berachain.com/developers/quickstart/#pre-requisites)

在开始之前，请确保您已准备好以下内容：

* Foundry工具包
* 你选择的文本编辑器

### 初始化Repository[​](https://docs.berachain.com/developers/quickstart/#initialize-repository)

首先，我们将使用Forge的`init`命令创建一个新项目：

```bash
forge init my_token;
```

这将创建一个名为`my_token`的新目录，其中包含基本的Forge项目结构和示例合约。如果使用VS Code作为文本编辑器，您可以添加`--vscode` flag，以初始化一些额外的默认设置。

```bash
forge init my_token --vscode;
```

现在您可以`cd`进入该目录，以便稍后运行代码：

```bash
cd my_token;
```

使用Foundry Forge格式化编写合约和测试合约，你可以随意删除下方生成的文件，因为本节不需要。

* `src/Counter.sol`
* `test/Counter.t.sol`
* `script/Counter.s.sol`

```bash
# FROM: ./my_token

rm src/Counter.sol test/Counter.t.sol script/Counter.s.sol;
```

### 安装依赖项[​](https://docs.berachain.com/developers/quickstart/#install-dependencies)

#### OpenZeppelin ERC-20[​](https://docs.berachain.com/developers/quickstart/#openzeppelin-erc-20)

OpenZeppelin提供了各种ERC代币标准（包括ERC-20）的常用接口和示例，这些代币经过审计和测试，因此可以使用他们的ERC-20标准接口来创建代币。这可以让我们更轻松地快速上手，而无需从头开始。

#### **Foundry**

如使用Foundry，请使用下方代码安装OpenZeppelin库：

```bash
# FROM: ./my_token

forge install openzeppelin/openzeppelin-contracts --no-commit;
```

上方代码将拉取`OpenZeppelin`请求，以暂存`.gitmodules`文件，并提交一条消息"Installed openzeppelin-contracts"。

要使用该库，请在项目的根目录下编辑 `remappings.txt`文件。

**文件位置**：`./remappings.txt`，运行以下代码：

```
ds-test/=lib/forge-std/lib/ds-test/src/
forge-std/=lib/forge-std/src/
@openzeppelin/=lib/openzeppelin-contracts/ // [!code++]
```

以上为了指引Foundry在编译合约时能正确调用`@openzeppelin`。

### 创建代币合约[​](https://docs.berachain.com/developers/quickstart/#create-the-token-contract)

现在你可以开始创建代币合约了，首先在`src/`文件夹中创建一个名为`MyToken.sol`的新文件。

```bash
# FROM: ./my_token

touch src/MyToken.sol;
```

然后，导入OpenZeppelin的ERC-20代币合约。

**文件位置：** `./src/MyToken.sol`，运行以下代码：

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

import “@openzeppelin/contracts/token/ERC20/ERC20.sol”;
```

这将从OpenZeppelin中导入`ERC20`代币合约，其中包含ERC-20代币标准中所有函数的基本功能实现，可以以此作为代币合约的基础。

接下来，将创建可供实际使用的代币合约，该合约在导入的ERC-20合约基础上扩展。

* 代币名称设置为“MyToken”
* 代币符号设置为“MT”
* 代币初始供应设置为1,000,000

**文件位置**：`./src/MyToken.sol`，运行以下代码：

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

import “@openzeppelin/contracts/token/ERC20/ERC20.sol”; 
import {ERC20} from “@openzeppelin/contracts/token/ERC20/ERC20.sol”; 

contract MyToken is ERC20 {
    uint256 public constant INITIAL_SUPPLY = 1_000_000 * 1 ether;

    constructor() ERC20(“MyToken”, “MT”){
        _mint(msg.sender, INITIAL_SUPPLY);
    }
}
```

{% hint style="info" %}
ERC-20代币标准的默认`小数位数`为18位，例如，`1ETH`只是以太坊代币的基本单位，还可以是`0.00000001ETH`。了解更多信息，请查看[OpenZeppelin Docs](https://docs.openzeppelin.com/contracts/3.x/erc20#a-note-on-decimals)\
上方合约部署可以解释为：创建了一个名为MyToken，代币符号为MT，代币初始供应量为100万，代币最小交易单位为小数点后18位的代币。
{% endhint %}

从技术上讲，完成以上操作，你已经成功创建代币！如果满意，你可以部署此合约，它会将100万个`$MT`代币发送到你部署合约的钱包(`msg.sender`)。接下来你可以随意处理这些代币，例如在Berachain BEX中将`$MT`与另一种代币创建流动性，以便其他用户可以交换获得`$MT`。

然而，我们通常希望代币的用途更广，以便脱颖而出。接下来，让我们为`$MT`代币添加更多功能。

### 设置转账销毁机制

通过重写OpenZeppelin `ERC20.sol`中的默认`_update`函数，添加一些常量。

**文件位置**：`ERC20.sol`，运行以下代码：

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    uint256 public constant INITIAL_SUPPLY = 1_000_000 * 1 ether;
    uint256 public constant BURN_PERCENTAGE = 1; // 1%
    address public constant BURN_ADDRESS = 0xDeaDbeefdEAdbeefdEadbEEFdeadbeEFdEaDbeeF; 

    constructor() ERC20("MyToken", "MT"){
        _mint(msg.sender, INITIAL_SUPPLY);
    }

    function _update(address sender, address recipient, uint256 amount) internal override { 
        uint256 burnAmount = (amount * BURN_PERCENTAGE) / 100;
        super._update(sender, recipient, amount - burnAmount);
        super._update(sender, BURN_ADDRESS, burnAmount);
    }
}
```

我们通过在`$MT`代币合约中使用`override` 修饰符重写了父合约 `_transfer`函数。我们仍然可以使用`super._transfer`调用父合约的默认`_transfer`函数，以在计算完销毁金额后运行实际的代币转账逻辑。

{% hint style="info" %}
上方合约部署可以解释为：每次转账时，合约会自动计算并销毁 1% 的代币，同时将剩余的 99% 转给接收者。
{% endhint %}

### 部署代币合约[​](https://docs.berachain.com/developers/quickstart/#deploy-token-contract)到Berachain

使用forge脚本将`$MT`代币合约部署到Berachain测试网。

```bash
# FROM: ./my_token

forge create --rpc-url https://bartio.rpc.berachain.com/ --private-key <YOUR_PRIVATE_KEY> src/MyToken.sol:MyToken --legacy;

# [Expected Output]:
# Deployer: 0x852Fc561Fd842ef1Af923ABfc64acC8A5624fe80
# Deployed to: 0x53E365fE5fDF332dD475E90bA8383B7F9853a49F
# Transaction hash: 0x59254ddcbb8dc1da89c7a1c7e300d8c6bd2f906b816b4497d046c717102d5725
```

### 验证代币合约[​](https://docs.berachain.com/developers/quickstart/#verifying-contract)

验证Berachain测试网上的`$MT`代币合约是否成功部署。

```bash
forge verify-contract 0x53E365fE5fDF332dD475E90bA8383B7F9853a49F src/MyToken.sol:MyToken --verifier-url 'https://api.routescan.io/v2/network/testnet/evm/80084/etherscan/api/' --etherscan-api-key "verifyContract" --num-of-optimizations 200

# [Expected Output]:
# Start verifying contract `0x53E365fE5fDF332dD475E90bA8383B7F9853a49F` deployed on mainnet
#
# Submitting verification for [src/MyToken.sol:MyToken] 0x53E365fE5fDF332dD475E90bA8383B7F9853a49F.
# Submitted contract for verification:
# Response: `OK`
# GUID: `321091ec-e529-5a11-a75c-cf1ffc6987d7`
# URL: https://etherscan.io/address/0x53e365fe5fdf332dd475e90ba8383b7f9853a49f
#
# !NOTE: Should be https://bartio.beratrail.io//address/0x53e365fe5fdf332dd475e90ba8383b7f9853a49f
```

### 后续步骤[​](https://docs.berachain.com/developers/quickstart/#next-steps)

现在，你已经掌握了如何使用Foundry将`ERC20`代币合约部署到Berachain测试网，请查看[开发者指南](../developer-guides/)，学习部署其他合约或构建dApp。
