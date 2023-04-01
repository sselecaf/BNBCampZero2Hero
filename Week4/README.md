# Week4 Homework

## 内容

简单实现了一个可更新的`Counter`合约，用来增减`Count`变量值

### Counter V1

实现`Counter`合约，第一个版本只有一个变量`Count`和一个方法`increaseCount`。`increaseCount`用来增加`Count`的计数。

### Counter V2

实现`Counter`合约，第二个版本增加了变量`lastChangeBlock`和一个方法`decreaseCount`。`lastChangeBlock`用来记录`Count`值最后一次改变是在哪个Block。`decreaseCount`用来减少`Count`的计数。


## 合约地址

ProxyAdmin：`0x41cd5b4b0cfbf3639f49b1eadd906cfc56404f79`

Proxy: `0x33b9421fbe8f50d49847d5cc5ecc478f8639c696`

CounterV1: `0x1cd76a0a3ed6da29cf4a7197eb94cd6e69503095`

CounterV2: `0x915b50af7fa573cad151c6611364631762200383`

## 交易哈希

部署ProxyAdmin：
`https://testnet.bscscan.com/tx/0x73548450b5ab76e5dac564d2c5549d1654f14ad2abae7b38b49939ca214036f8`

部署Proxy:
`https://testnet.bscscan.com/tx/0x28c7951428febe009f80417caf2bbd0b94bb68f76d1dffbd2f66faa114a5c804`

部署CounterV1:
`https://testnet.bscscan.com/tx/0x529f132ebbd544cb25bb900e8b3546dfd6f14ce62f15ae380168bae40f7c75cd`

部署CounterV2:
`https://testnet.bscscan.com/tx/0xed692dd044715159068838af3034bd768e8bf21c098eec9ebaaec5f07ed256c9`

## 相关操作

### 部署ProxyAdmin合约

`npx hardhat deploy --network bsctest --tags ProxyAdmin`

### 部署Counter合约

`npx hardhat deploy --network bsctest --tags Counter`

### 合约验证

```
npx hardhat verify --network bsctest 0x1cd76a0a3ed6da29cf4a7197eb94cd6e69503095

npx hardhat verify --network bsctest 0x41cd5b4b0cfbf3639f49b1eadd906cfc56404f79

npx hardhat verify --network bsctest 0x33b9421fbe8f50d49847d5cc5ecc478f8639c696
```

### 执行Task

```
npx hardhat --network bsctest increaseCount --proxy 0x33b9421fbe8f50d49847d5cc5ecc478f8639c696

npx hardhat --network bsctest decreaseCount --proxy 0x33b9421fbe8f50d49847d5cc5ecc478f8639c696
```