基金合约实现


## Functions
### deposit
```solidity
  function deposit(
    uint256 amount
  ) external returns (uint256 share)
```
用户存入基金的本币。

充值功能适用于ERC20资金，如果是ETH资金（内部转为WETH9），直接转入ETH给合约即可。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint256 | 存入数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`share`| uint256 | 用户获得的基本份额代币数量
### _deposit
```solidity
  function _deposit(
    uint amount, 
    uint total_assets
  ) internal returns (uint256 share)
```
保存用户基金存入状态信息。

返回基金份额信息。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint256 | 存入数量
|`total_assets` | uint256 | 基金总资产


### receive
```solidity
  function receive() external payable
```
用户直接转账ETH进行投资

### withdraw
```solidity
  function withdraw(
    uint256 share,
    uint256 amountMin,
    uint256 deadline
  ) external returns (uint256 amount)
```
用户提取指定份额的投资


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`share` | uint256 | 要提前的基金份额代币数量
|`amountMin` | uint256 | 最小领取数量
|`deadline` | uint256 | 交易截止时间

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | 返回提取的基金本币数量
### poolsLength
```solidity
  function poolsLength() external returns (uint256)
```
获取池子数组长度


### positionsLength
```solidity
  function positionsLength(
    uint256 poolIndex
  ) external returns (uint256)
```
获取指定池子的头寸数组长度


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置

### setDescriptor
```solidity
  function setDescriptor(
    bytes _descriptor
  ) external
```
设置基金的描述信息，32 bytes的基金名称 + 任意长度的基金描述。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_descriptor` | bytes | 32 bytes的基金名称 + 任意长度的基金描述

### setDepositDeadline
```solidity
  function setDepositDeadline(
    uint256 deadline
  ) external
```
设置基金可存入的截止时间。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`deadline` | uint256 | 截止时间

### setPath
```solidity
  function setPath(
    address distToken,
    bytes buy,
    bytes sell
  ) external
```
设置基金中的代币交易路径。

修改sellPath需要先清空相关池子的资产。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`distToken` | address | 目标代币地址
|`buy` | bytes | 购买路径 (fundToken->distToken)
|`sell` | bytes | 卖出路径 (distToken->fundToken)

### uniswapV3MintCallback
```solidity
  function uniswapV3MintCallback(
    uint256 amount0Owed,
    uint256 amount1Owed,
    bytes data
  ) external
```

在从 IUniswapV3Pool#mint 将流动性铸造到头寸指定后回调 `msg.sender`的该方法，以处理后续转账操作。

在实施中，您必须支付因铸造流动性而欠下的池子代币。
必须检查此方法的调用者是否是由规范 UniswapV3Factory 部署的 UniswapV3Pool。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount0Owed` | uint256 | 需要转给池子的 token0 数量
|`amount1Owed` | uint256 | 需要转给池子的 token1 数量
|`data` | bytes | 调用者通过 IUniswapV3PoolActions#mint 调用传递的任何数据

### init
```solidity
  function init(
    address token0,
    address token1,
    uint24 fee,
    int24 tickLower,
    int24 tickUpper,
    uint256 amount,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
初始化一个基金头寸，investment大于0时会投资该数量的基金本币到该头寸。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token0` | address | 池子的token0地址
|`token1` | address | 池子的token1地址
|`fee` | uint24 | 池子fee
|`tickLower` | int24 | 头寸的tickLower价格下界
|`tickUpper` | int24 | 头寸的tickUpper价格上界
|`amount` | uint256 | 初始投资金额，允许为0，0表示只初始化仓位，不进行实质性投资
|`maxPIS` | uint32 | 最大交易滑点和价格影响

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| address | 添加头寸获得LP数量
### add
```solidity
  function add(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 amount,
    bool collect,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
投资指定头寸，可选择是否复投之前的收益。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`positionIndex` | uint256 | 头寸索引位置
|`amount` | uint256 | 投资基金本币数量
|`collect` | bool | 是否复投
|`maxPIS` | uint32 | 最大交易滑点和价格影响

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| uint256 | 添加头寸获得LP数量
### sub
```solidity
  function sub(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 proportionX128,
    uint32 maxPIS
  ) external returns (uint256 amount)
```
撤资指定的头寸。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`positionIndex` | uint256 | 头寸索引位置
|`proportionX128` | uint256 | 撤资百分比，左移 128 位； 0是允许的，0表示只收取手续费
|`maxPIS` | uint32 | 最大交易滑点和价格影响

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | 撤资获得的基金本币金额
### move
```solidity
  function move(
    uint256 poolIndex,
    uint256 subIndex,
    uint256 addIndex,
    uint256 proportionX128,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
调整头寸资金，从一个头寸移动到另一个头寸。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`subIndex` | uint256 | 要移除资金的头寸索引位置
|`addIndex` | uint256 | 要追加资金的头寸索引位置
|`proportionX128` | uint256 | 调整比例，左移128位
|`maxPIS` | uint32 | 最大交易滑点和价格影响

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| uint256 | 添加头寸获得LP数量 after completion
### assetsOfPosition
```solidity
  function assetsOfPosition(
    uint256 poolIndex,
    uint256 positionIndex
  ) public returns (uint256 amount)
```
获取指定头寸的资产数量


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`positionIndex` | uint256 | 头寸索引位置

### assetsOfPool
```solidity
  function assetsOfPool(
    uint256 poolIndex
  ) public returns (uint256 amount)
```
获取指定池子的资产数量


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置

### totalAssets
```solidity
  function totalAssets() public returns (uint256 amount)
```
获取基金总的资产。

以基金本币计价的总资产金额。


### _assetsOfPool
```solidity
  function _assetsOfPool(
    uint poolIndex
  ) internal returns (uint256 amount, uint256[])
```
获取指定池子的资产

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置


