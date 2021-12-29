本接口包含可由控制器合约调用的基金管理方法。


## Functions
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

目标代币必须是受信任的才可被设置。

该函数只能被控制器调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`distToken` | address | 目标代币地址
|`buy` | bytes | 购买路径 (fundToken->distToken)
|`sell` | bytes | 卖出路径 (distToken->fundToken)

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
|`liquidity`| uint256 | 完成后增加的LP数量

