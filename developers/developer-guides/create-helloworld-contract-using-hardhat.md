# 使用 Hardhat 部署 HelloWorld 合约

本节将展示如何使用[Hardhat](https://hardhat.org/)创建新的Solidity合约，配置Berachain网络详细信息，部署合约到Berachain以及进行合约验证。这里是本节的代码仓库：[Berachain GitHub Project Code Repository](https://github.com/berachain/guides/tree/main/apps/hardhat-viem-helloworld)。

### 先决条件

开始之前，请确保你的本地设备上满足以下条件：

* 浏览器钱包账户拥有$BERA 代币（用于部署）
* NVM, Node,  `v18.18.2`（三选一）
* `pnpm`, `yarn`, `npm`（三选一）

### 创建HelloWorld代码 <a href="#creating-helloworld-project-code-setup" id="creating-helloworld-project-code-setup"></a>

首先，为HelloWorld创建一个新的文件夹：

```bash
mkdir create-helloworld-contract-using-hardhat;
cd create-helloworld-contract-using-hardhat;
```

然后，启动`Hardhat`，并创建`viem`模板：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

npx hardhat init;

# [Expected Prompts]:
# 888    888                      888 888               888
# 888    888                      888 888               888
# 888    888                      888 888               888
# 8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
# 888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
# 888    888 .d888888 888    888  888 888  888 .d888888 888
# 888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
# 888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888
#
# 👷 Welcome to Hardhat v2.18.3 👷‍
#
# ✔ What do you want to do? · Create a TypeScript project (with Viem)
# ✔ Hardhat project root: · /path/to/create-helloworld-contract-using-hardhat
# ✔ Do you want to add a .gitignore? (Y/n) · y
# ✔ Do you want to install this sample project's dependencies with npm (hardhat @nomicfoundation/#  hardhat-toolbox-viem)? (Y/n) · y
```

安装`dotenv`依赖项，以便使用环境变量。

```bash
# FROM ./create-helloworld-contract-using-hardhat;

pnpm add -D dotenv;
```

### 创建HelloWorld合约 <a href="#creating-the-helloworld-contract" id="creating-the-helloworld-contract"></a>

上述操作，Hardhat创建了需要的文件。现在，已经准备好一切，可以创建一个新的Solidity合约了。

首先，将Hardhat创建的文件重命名为`HelloWorld.sol`：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

# Renames `Lock.sol` to `HelloWorld.sol`
mv contracts/Lock.sol contracts/HelloWorld.sol;
```

然后，替换重命名的`HelloWorld.sol`文件中的现有代码。

**文件位置**：`./contract/HelloWorld.sol`，运行以下代码：

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

contract HelloWorld {
    // Events that allows for emitting a message
    event NewGreeting(address sender, string message);

    // Variables
    string greeting;

    // Main constructor run at deployment
    constructor(string memory _greeting) {
        greeting = _greeting;
        emit NewGreeting(msg.sender, _greeting);
    }

    // Get function
    function getGreeting() public view returns (string memory) {
        return greeting;
    }

    // Set function
    function setGreeting(string memory _greeting) public {
        greeting = _greeting;
        emit NewGreeting(msg.sender, _greeting);
    }
}
```

我们已经创建了一个新的Solidity合约，接下来测试合约能否成功编译：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

npx hardhat compile;

# [Expected Output]:
# Compiled 1 Solidity file successfully (evm target: paris).
```

你还可以通过对`package.json`文件进行一些修改，简化编译步骤。

**文件位置**：`./package.json`，运行以下代码：

```json
{
  "name": "create-helloworld-contract-using-hardhat",
  "scripts": {

    "compile": "./node_modules/.bin/hardhat compile"
  }, 
  "devDependencies": {
    "@nomicfoundation/hardhat-toolbox-viem": "^1.0.0",
    "dotenv": "^16.3.1",
    "hardhat": "^2.18.3"
  }
}
```

现在，可以使用下方代码编译合约：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

pnpm compile; # npm run compile or yarn run compil;

# [Expected Output]:
# Nothing to compile
```

### 测试HelloWorld合约 <a href="#testing-the-helloworld-contract" id="testing-the-helloworld-contract"></a>

合约成功创建后，需要通过编写一些测试程序来确保合约能正常运行。

首先，重命名Hardhat在`/test`目录中创建的测试文件：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

# Renames `Lock.ts` to `HelloWorld.test.ts`
mv test/Lock.ts test/HellWorld.test.ts;
```

然后，替换重命名的`HelloWorld.test.ts`文件中的现有代码。

**文件位置**：`./test/HelloWorld.test.ts`，运行以下代码：

```tsconfig
// Imports
// ========================================================
import { loadFixture } from "@nomicfoundation/hardhat-toolbox-viem/network-helpers";
import { expect } from "chai";
import hre from "hardhat";

// Tests
// ========================================================
describe("HelloWorld", function () {
  // We define a fixture to reuse the same setup in every test.
  // We use loadFixture to run this setup once, snapshot that state,
  // and reset Hardhat Network to that snapshot in every test.
  async function deployFixture() {
    // Contracts are deployed using the first signer/account by default
    const [owner, otherAccount] = await hre.viem.getWalletClients();

    const contract = await hre.viem.deployContract("HelloWorld", [
      "Test Message",
    ]);
    const publicClient = await hre.viem.getPublicClient();

    return {
      owner,
      otherAccount,
      publicClient,
      contract,
    };
  }

  /**
   *
   */
  describe("Deployment", function () {
    /**
     *
     */
    it("Should deploy with original message", async function () {
      // Setup
      const { contract } = await loadFixture(deployFixture);

      // Init + Expectations
      expect(await contract.read.getGreeting()).to.equal("Test Message");
    });

    /**
     *
     */
    it("Should set a new message", async function () {
      // Setup
      const { contract, owner } = await loadFixture(deployFixture);

      // Init
      await contract.write.setGreeting(["Hello There"]);

      // Expectations
      expect(await contract.read.getGreeting()).to.equal("Hello There");
    });
  });
});
```

接下来，运行下方代码以运行测试程序：

```bash
# FROM ./create-helloworld-contract-using-hardhat;

npx hardhat test;

# [Expected Output]:
#   HelloWorld
#     Deployment
#       ✔ Should deploy with original message (2723ms)
#       ✔ Should set a new message
#
#
#   2 passing (3s)
```

你还可以通过对`package.json`文件进行一些修改，以便更轻松地运行`pnpm test`测试程序。

**文件位置**：`./package.json`，运行以下代码：

```json
{
  "name": "create-helloworld-contract-using-hardhat",
  "scripts": {
    "compile": "./node_modules/.bin/hardhat compile",
    "test": "./node_modules/.bin/hardhat test"
  },
  "devDependencies": {
    "@nomicfoundation/hardhat-toolbox-viem": "^1.0.0",
    "dotenv": "^16.3.1",
    "hardhat": "^2.18.3"
  }
}
```

### 为Berachain配置Hardhat

{% hint style="info" %}
通过Hardhat创建viem模板的方式部署的合约，目前尚未完全支持开箱即用的自定义链，但在 Berachain主网启动后将会支持。
{% endhint %}

首先，为了正确设置`hardhat.config.ts`，需要使用`dotenv`安装包创建一个`.env`文件，用于声明环境变量，供配置读取。

```bash
# FROM ./create-helloworld-contract-using-hardhat;

touch .env;
```

然后，在新建的`.env`文件中，运行以下代码，**文件位置**：`./.env`。

```bash
# Chain Configurations
CHAIN_ID=80084
NETWORK_NAME="berachainbArtio"
CURRENCY_DECIMALS=18
CURRENCY_NAME="BERA Token"
CURRENCY_SYMBOL="BERA"

# API key for Beratrail Block Explorer, can be any value for now
BLOCK_EXPLORER_NAME=Beratrail Block Explorer
BLOCK_EXPLORER_API_KEY=xxxxx
BLOCK_EXPLORER_API_URL=https://api.routescan.io/v2/network/testnet/evm/80084/etherscan/api/
BLOCK_EXPLORER_URL=https://bartio.beratrail.io/

# Wallet + RPC configurations
RPC_URL=https://bartio.rpc.berachain.com/
# Private key generated from Hardhat local - replace with Berachain
# NEVER SHARE THIS WITH ANYONE AND AVOID COMMITTING THIS WITH YOUR GIT REPOSITORY
WALLET_PRIVATE_KEY=0xYOUR_WALLET_PRIVATE_KEY
```

{% hint style="info" %}
代币合约参数支持自定义，总体配置步骤是相同的。
{% endhint %}

设置好环境变量后，需要将它们加载到`hardhat.config.ts`文件。

**文件位置**：`./hardhat.config.ts`，运行以下代码：

```tsconfig
// Imports
// ========================================================
import { HardhatUserConfig } from "hardhat/config";
import "@nomicfoundation/hardhat-toolbox-viem";
import dotenv from "dotenv";

// Load Environment Variables
// ========================================================
dotenv.config();

// Main Hardhat Config
// ========================================================
const config: HardhatUserConfig = {
  solidity: "0.8.19",
  networks: {
    // For localhost network
    hardhat: {
      chainId: 1337,
    },
    // NOTE: hardhat viem currently doesn't yet support this method for custom chains through Hardhat config ↴
    berachainTestnet: {
      chainId: parseInt(`${process.env.CHAIN_ID}`),
      url: `${process.env.RPC_URL || ""}`,
      accounts: process.env.WALLET_PRIVATE_KEY
        ? [`${process.env.WALLET_PRIVATE_KEY}`]
        : [],
    },
  },
};

// Exports
// ========================================================
export default config;
```

### 在Berachain部署HelloWorld合约 <a href="#deploying-helloworld-contract" id="deploying-helloworld-contract"></a>

我们已经完成了所有配置设置，现在尝试运行一个本地节点，并将其部署到本地环境。

首先，通过对`package.json`文件进行一些修改，让部署运行更轻松。

**文件位置**： `./package.json`，运行以下代码：

```json
{
  "name": "create-helloworld-contract-using-hardhat",
  "scripts": {
    "compile": "./node_modules/.bin/hardhat compile",
    "node": "./node_modules/.bin/hardhat node", 
    "deploy:localhost": "./node_modules/.bin/hardhat run scripts/deploy.ts --network localhost", 
    "deploy:berachain": "./node_modules/.bin/hardhat run scripts/deploy.ts --network berachainTestnet", 
    "test": "./node_modules/.bin/hardhat test"
  },
  "devDependencies": {
    "@nomicfoundation/hardhat-toolbox-viem": "^1.0.0",
    "dotenv": "^16.3.1",
    "hardhat": "^2.18.3"
  }
}
```

接下来，配置`./scripts/deploy.ts`脚本，以确保合约正确部署。

**文件位置**： `./scripts/deploy.ts`，运行以下代码：

```tsconfig
// Imports
// ========================================================
import hre from "hardhat";

// Main Deployment Script
// ========================================================
async function main() {
  const contract = await hre.viem.deployContract("HelloWorld", [
    "Hello from the contract!",
  ]);
  console.log(`HelloWorld deployed to ${contract.address}`);
}

// Init
// ========================================================
// We recommend this pattern to be able to use async/await everywhere
// and properly handle errors.
main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

部署脚本配置好后，我们可以在一个终端运行本地节点，并在另一个终端部署合约。

#### 终端 1：部署合约

```bash
# FROM ./create-helloworld-contract-using-hardhat;

pnpm node;

# [Expected Output]:
# Started HTTP and WebSocket JSON-RPC server at http://127.0.0.1:8545/
#
# Accounts
# ========
#
# WARNING: These accounts, and their private keys, are publicly known.
# Any funds sent to them on Mainnet or any other live network WILL BE LOST.
#
# Account #0: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000 ETH)
# Private Key: 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80bash
```

复制上方代码中的私钥`Private Key`并将其粘贴到 `.env` 文件中，作为`WALLET_PRIVATE_KEY`。

**文件位置**：`./.env`，运行以下代码：

```bash
WALLET_PRIVATE_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```

#### 终端 2：运行本地节点

```bash
# FROM ./create-helloworld-contract-using-hardhat;

pnpm deploy:localhost;
# [Expected Similar Output]:
# HelloWorld deployed to 0x5fbdb2315678afecb367f032d93f642f64180aa3
```

现在，合约已成功部署到本地节点，接下来配置部署脚本，以便合约直接部署到Berachain网络。

{% hint style="info" %}
要使viem支持自定义链，需要进行额外配置，下方代码展示了如何为Berachain设置额外配置。当Berachain主网上线时，这些额外配置可能不再需要。
{% endhint %}

**文件位置**：`./scripts/deploy.ts`，运行以下代码：

```tsconfig
// Imports
// ========================================================
import hre from "hardhat";
import fs from "fs"; 
import { defineChain } from "viem"; 
import { privateKeyToAccount } from "viem/accounts"; 

// Config Needed For Custom Chain
// ========================================================
const chainConfiguration = defineChain({

  id: parseInt(`${process.env.CHAIN_ID}`), 
  name: `${process.env.NETWORK_NAME}`, 
  network: `${process.env.NETWORK_NAME}`, 
  nativeCurrency: {

    decimals: parseInt(`${process.env.CURRENCY_DECIMALS}`), 
    name: `${process.env.CURRENCY_NAME}`, 
    symbol: `${process.env.CURRENCY_SYMBOL}`, 
  }, 
  rpcUrls: {

    default: {

      http: [`${process.env.RPC_URL}`], 
    }, 
    public: {

      http: [`${process.env.RPC_URL}`], 
    }, 
  }, 
  blockExplorers: {

    default: {
      name: `${process.env.BLOCK_EXPLORER_NAME}`,
      url: `${process.env.BLOCK_EXPLORER_URL}`,
    }, 
  }, 
}); 

// Main Deployment Script
// ========================================================
async function main() {
  // NOTE: hardhat with viem currently doesn't support custom chains so there needs to be some custom functionality ↴
  if (hre.network.name === "berachainTestnet") {

    // Retrieve contract artifact ABI & Bytecode
    const contractName = "HelloWorld"; 
    const artifactFile = fs.readFileSync(
      `${hre.artifacts._artifactsPath}/contracts/${contractName}.sol/${contractName}.json`
    ); 
    const artifactJSON = JSON.parse(artifactFile.toString()) as any; 

    // Configure wallet client
    const walletClient = await hre.viem.getWalletClient(

      // wallet account
      privateKeyToAccount(hre.network.config.accounts?.[0] as `0x${string}`), 
      // configured chain
      {

        chain: chainConfiguration, 
      } 
    ); 

    // Deploy contract
    const hash = await walletClient.deployContract({

      abi: artifactJSON.abi, 
      bytecode: artifactJSON.bytecode, 
      args: ["Hello From Deployed Contract"], 
    }); 
    console.log({ hash }); 

    // Retrieve deployed contract address
    const publicClient = await hre.viem.getPublicClient({

      chain: chainConfiguration, 
    }); 
    const receipt = await publicClient.waitForTransactionReceipt({ hash }); 
    console.log(`${contractName} deployed to ${receipt?.contractAddress}`); 
  } else {

    const contract = await hre.viem.deployContract("HelloWorld", [
      "Hello from the contract!",
    ]);
    console.log(`HelloWorld deployed to ${contract.address}`);
  } 
}

// Init
// ========================================================
// We recommend this pattern to be able to use async/await everywhere
// and properly handle errors.
main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

接下来，将`WALLET_PRIVATE_KEY`替换为一个拥有`$BERA`代币的钱包，可以从[Berachain测试网水龙头](../../learn/native-dapps/testnet-faucet.md)获取测试网`$BERA`代币。

**文件位置**：`./.env`，运行以下代码：

```bash
WALLET_PRIVATE_KEY=0xYOUR_WALLET_PRIVATE_KEY
```

现在，可以直接将合约部署到Berachain了。

```bash
# FROM ./create-helloworld-contract-using-hardhat;

pnpm deploy:berachain;

# [Expected Similar Output]:
# {
#   hash: '0x3ff0120c126b20d9f286657521c9d2d1edbb38f60dcd5fc6b95638a192588182'
# }
# HelloWorld deployed to 0x38f8423cc4390938c01616d7a9f761972e7f116a
```

你可以运行下方代码，在Berachain Beratrail区块浏览器中查看部署的合约：

```bash
open https://bartio.beratrail.io/address/0x38f8423cc4390938c01616d7a9f761972e7f116a

# [Expected Result Should Open Your Browser]
```

你会看到合约已经成功部署，但未被验证，因为它仍显示合约字节码，接下来需要验证合约。

### 验证HelloWorld合约 <a href="#verifying-helloworld-contract" id="verifying-helloworld-contract"></a>

为了验证合约，需要在`hardhat.config.ts`文件中添加一个额外配置。

**文件位置**：`./hardhat.config.ts`，运行以下代码：

```tsconfig
// Imports
// ========================================================
import { HardhatUserConfig } from "hardhat/config";
import "@nomicfoundation/hardhat-toolbox-viem";
import dotenv from "dotenv";

// Load Environment Variables
// ========================================================
dotenv.config();

// Main Hardhat Config
// ========================================================
const config: HardhatUserConfig = {
  solidity: "0.8.19",
  networks: {
    hardhat: {
      chainId: 1337,
    },
    // NOTE: hardhat viem currently doesn't yet support this method for custom chains through Hardhat config ↴
    berachainTestnet: {
      chainId: parseInt(`${process.env.CHAIN_ID}`),
      url: `${process.env.RPC_URL || ""}`,
      accounts: process.env.WALLET_PRIVATE_KEY
        ? [`${process.env.WALLET_PRIVATE_KEY}`]
        : [],
    },
  }, 
  // For Contract Verification
  etherscan: {

    apiKey: `${process.env.BLOCK_EXPLORER_API_KEY}`, 
    customChains: [

      {

        network: "Berachain Testnet", 
        chainId: parseInt(`${process.env.CHAIN_ID}`), 
        urls: {

          apiURL: `${process.env.BLOCK_EXPLORER_API_URL}`, 
          browserURL: `${process.env.BLOCK_EXPLORER_URL}`, 
        }, 
      }, 
    ], 
  }, 
};

// Exports
// ========================================================
export default config;
```

完成额外配置后，通过向`package.json`添加 run 命令来查看更改。

**文件位置**：`./package.json`，运行以下代码：

```json
{
  "name": "create-helloworld-contract-using-hardhat",
  "scripts": {
    "compile": "./node_modules/.bin/hardhat compile",
    "node": "./node_modules/.bin/hardhat node",
    "deploy:localhost": "./node_modules/.bin/hardhat run scripts/deploy.ts --network localhost",
    "deploy:berachain": "./node_modules/.bin/hardhat run scripts/deploy.ts --network berachainTestnet",
    "test": "./node_modules/.bin/hardhat test",
    "verify": "./node_modules/.bin/hardhat verify --network berachainTestnet"
  },
  "devDependencies": {
    "@nomicfoundation/hardhat-toolbox-viem": "^1.0.0",
    "dotenv": "^16.3.1",
    "hardhat": "^2.18.3"
  }
}
```

最后，使用合约部署地址和初始参数`Hello From Deployed Contract`，运行下方代码验证合约。

```bash
# FROM ./create-helloworld-contract-using-hardhat;

# Equivalent to: npx hardhat verify 0x38f8423cc4390938c01616d7a9f761972e7f116a "Hello From Deployed Contract"
pnpm verify 0x38f8423cc4390938c01616d7a9f761972e7f116a "Hello From Deployed Contract";

# [Expected Output]:
#
# Successfully submitted source code for contract
# contracts/HelloWorld.sol:HelloWorld at 0x38f8423cc4390938c01616d7a9f761972e7f116a
# for verification on the block explorer. Waiting for verification result...
#
# Successfully verified contract HelloWorld on the block explorer.
# https://bartio.beratrail.io/address/0x38f8423cc4390938c01616d7a9f761972e7f116a#code
```

在Beratail可以看到，合约已成功验证，并且可以查看到合约Solidity代码。

### 完整代码库 <a href="#full-code-repository" id="full-code-repository"></a>

{% embed url="https://github.com/berachain/guides/tree/main/apps/hardhat-viem-helloworld" %}
