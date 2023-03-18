# Week2 Homework
作业内容：部署流动性挖矿合约

### 1. 部署ERC-20合约
- AAA token 合约代码：[aaa.sol](https://github.com/sselecaf/BNBCampZero2Hero/blob/main/Week2/aaa.sol)

- 部署transaction： [0x58badee5ec2ca805cb19db4f81b58dc27f9832699dacf947be8d31888efcc6a5](https://testnet.bscscan.com/tx/0x58badee5ec2ca805cb19db4f81b58dc27f9832699dacf947be8d31888efcc6a5)

- 部署地址：[0x819b90dc1309cf956783213324480310794aea44](https://testnet.bscscan.com/address/0x819b90dc1309cf956783213324480310794aea44)

### 2. 完成流动性挖矿合约的部署

#### 合约部署

- BBB Token，该token作为奖励流动性挖矿奖励token，通过LPStaking合约mint新增的BBB token
  - 合约代码：[BBB.sol](https://github.com/sselecaf/BNBCampZero2Hero/blob/main/Week2/BBB.sol)
  
  - 部署transaction：[0xa6c58fea93d35d4b8b537450aeb46bebd6a811564394e7a051b4dd015c7531c4](https://testnet.bscscan.com/tx/0xa6c58fea93d35d4b8b537450aeb46bebd6a811564394e7a051b4dd015c7531c4)
  
  - 部署地址：[0x6b8bea3e57bf88988772b748a2125ec21e9d2a1a](https://testnet.bscscan.com/address/0x6b8bea3e57bf88988772b748a2125ec21e9d2a1a)

- 流动性挖矿合约

  - 合约代码：[LPStaking.sol](https://github.com/sselecaf/BNBCampZero2Hero/blob/main/Week2/LPStaking.sol)

  - 部署transaction：[0x1fe03ee7405260d7ca754b8d55fffe51e47f6446d45faf5fb69cfef5950a81e5](https://testnet.bscscan.com/tx/0x1fe03ee7405260d7ca754b8d55fffe51e47f6446d45faf5fb69cfef5950a81e5)

  - 部署地址：[0xaf0589386dd1da00cbf30e6d5bb486779bd17e80](https://testnet.bscscan.com/tx/0x1fe03ee7405260d7ca754b8d55fffe51e47f6446d45faf5fb69cfef5950a81e5)

#### 该合约包含了以下功能：

- 添加池子：每个池子包含一个 LP Token 和分配给该池子的 allocPoint（权重）。

- 设置池子：更改池子的 allocPoint。

- 存款：将 LP Token 存入池子，获得对应的代币奖励。存款时将会自动计算之前未领取的奖励并发送给用户。

- 提款：从池子中提取 LP Token，并领取对应的代币奖励。提款时将会自动计算之前未领取的奖励并发送给用户。

- 紧急提款：从池子中提取 LP Token，但不会领取奖励。这个功能应该只在必要时使用

#### 相关Transaction

- 调用 BBB Token 合约的 Add Minter 方法添加 minter 地址
  - [0xcdec2904afd023d02570f1bfb2fd598ca119472c4343ebfcda36c33fc6acc348](https://testnet.bscscan.com/tx/0xcdec2904afd023d02570f1bfb2fd598ca119472c4343ebfcda36c33fc6acc348)
- 调用 LPStaking 合约的 Add Pool 方法添加一个流动性挖矿的Pool，Pool 支持的质押 LP token 为 AAA Token，并设置 Pool 的权重为 100
  - [0x2203aade1a98d1989ddeea57d6a8e9d1c5817ad80671f0d5cc6ca7bd5cfa67a1](https://testnet.bscscan.com/tx/0x2203aade1a98d1989ddeea57d6a8e9d1c5817ad80671f0d5cc6ca7bd5cfa67a1)
- 调用 AAA Token 的 Approve 方法，授权 LPStaking 合约使用 100个 AAA token：
  - [0x68eb62c75c29fc869e329a17132321b054f4680f53159b6c832c2ea9cd44bcb0](https://testnet.bscscan.com/tx/0x68eb62c75c29fc869e329a17132321b054f4680f53159b6c832c2ea9cd44bcb0)
- 调用 LPStaking 合约的 Deposit 方法，往刚刚添加的 Pool 质押100个 AAA token：
  - [0xed5b1b46c3e3957fbfb13e1cd6660bbe39b5ae9c581ffa09df82a86e7cdf6337](https://testnet.bscscan.com/tx/0xed5b1b46c3e3957fbfb13e1cd6660bbe39b5ae9c581ffa09df82a86e7cdf6337)
- 调用 LPStaking 合约的 Deposit 方法，提取流动性挖矿奖励，获得400个BBB token：
  - [0xf96d0bfef76354289e5e7a0828b9bef522bd6239385de429d5bec7124ae0c309](https://testnet.bscscan.com/tx/0xf96d0bfef76354289e5e7a0828b9bef522bd6239385de429d5bec7124ae0c309)
