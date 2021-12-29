本接口包含任何人都可以调用的状态变量和只读方法。


## Functions
### controller
```solidity
  function controller() external returns (address)
```
返回控制器合约地址


### manager
```solidity
  function manager() external returns (address)
```
返回基金经理地址


### token
```solidity
  function token() external returns (address)
```
返回基金本币地址


### descriptor
```solidity
  function descriptor() external returns (bytes)
```
返回 32 字节的基金名称 + 任意长度的简要说明


### lockPeriod
```solidity
  function lockPeriod() external returns (uint256)
```
返回基金存入锁定期



### baseLine
```solidity
  function baseLine() external returns (uint256)
```
返回基金收费基线


### managerFee
```solidity
  function managerFee() external returns (uint256)
```
返回基金经理收益分成比例



### depositDeadline
```solidity
  function depositDeadline() external returns (uint256)
```
返回基金可存入截止时间



### lastDepositTime
```solidity
  function lastDepositTime(
    address account
  ) external returns (uint256)
```
查询用户`account`的最新存入时间


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`account` | address | 要查询的目标地址

### totalInvestment
```solidity
  function totalInvestment() external returns (uint256)
```
返回总的投入本金



### investmentOf
```solidity
  function investmentOf(
    address owner
  ) external returns (uint256)
```
返回用户`owner`的投资本金


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`owner` | address | 要查询的目标地址

### assetsOfPosition
```solidity
  function assetsOfPosition(
    uint256 poolIndex,
    uint256 positionIndex
  ) external returns (uint256)
```
获取指定头寸的基金本币资产数量


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`positionIndex` | uint256 | 头寸索引位置

### assetsOfPool
```solidity
  function assetsOfPool(
    uint256 poolIndex
  ) external returns (uint256)
```
获取指定池子的基金本币资产数量


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置

### totalAssets
```solidity
  function totalAssets() external returns (uint256)
```
获取基金总的基金本币数量。

该数量是用基金本币衡量的资产数量。


### buyPath
```solidity
  function buyPath(
    address _token
  ) external returns (bytes)
```
用基金本币购买某币的交易路径。

交易路径是Uniswap V3 兑换代币路径格式。


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_token` | address | 目标代币

### sellPath
```solidity
  function sellPath(
    address _token
  ) external returns (bytes)
```
兑换代币成基金本币的交易路径。

交易路径是Uniswap V3 兑换代币路径格式。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_token` | address | 目标代币

### pools
```solidity
  function pools(
    uint256 index
  ) external returns (address)
```
查询指定索引位置的池子地址


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`index` | uint256 | 池子索引位置

### positions
```solidity
  function positions(
    uint256 poolIndex,
    uint256 positionIndex
  ) external returns (bool isEmpty, int24 tickLower, int24 tickUpper)
```
获取指定位置的头寸信息

由于基金需要遍历所有头寸，所以使用二维动态数组来存储头寸。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置
|`positionIndex` | uint256 | 池子索引位置

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isEmpty`| bool | 是否是一个空头寸
|`tickLower`| uint256 | tick上界
|`tickUpper`| uint256 | tick下界

### poolsLength
```solidity
  function poolsLength() external returns (uint256)
```
获取基金总的池子长度



### positionsLength
```solidity
  function positionsLength(
    uint256 poolIndex
  ) external returns (uint256)
```
获取指定池子的所有头寸长度


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | 池子索引位置


