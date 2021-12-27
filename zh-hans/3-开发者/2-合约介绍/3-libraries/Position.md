一个用于操作头寸流动性增减和资产数额查询的库。


## Functions
### getAmountsForAmount0
```solidity
  function getAmountsForAmount0(
    uint160 sqrtPriceX96,
    uint160 sqrtPriceL96,
    uint160 sqrtPriceU96,
    uint256 deltaX
  ) internal returns (uint256 amount0, uint256 amount1)
```
计算将 t0 最大化添加到池子头寸中，所需的 t0 和 t1 数量。

计算公式：DeltaX0 = DeltaX0 /( SPu*(SPc-SPl) / (SPc*(SPu-SPc)) + 1)

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`sqrtPriceX96` | uint160 | 当前池子的sqrt价格
|`sqrtPriceL96` | uint160 | 头寸下边界的sqrt价格
|`sqrtPriceU96` | uint160 | 头寸上边界的sqrt价格
|`deltaX` | uint256 | Delta amount of token0

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint160 | token0数量
|`amount1`| uint160 | token1数量
### getAmountOutMin
```solidity
  function getAmountOutMin(
    uint256 curSqrtPirceX96,
    uint256 maxPriceImpact,
    uint256 amountIn
  ) internal returns (uint256 amountOutMin)
```
计算最小交易输出值


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`curSqrtPirceX96` | uint256 | 当前池子的sqrt价格
|`maxPriceImpact` | uint256 | 最大价格影响值
|`amountIn` | uint256 | 输入代币数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amountOutMin`| uint256 | 最小输出值
### computeSwapAmounts
```solidity
  function computeSwapAmounts(
    struct Position.SwapParams params,
    mapping(address => bytes) buyPath
  ) internal returns (uint256 amount0Max, uint256 amount1Max)
```
根据基金的本币数量和收取的费用t0,t1，计算两个代币在指定投资头寸上的分配数量。


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.SwapParams | 头寸交易参数
|`buyPath` | mapping(address => bytes) | 购买其它代币的路径

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0Max`| uint256 | 最大获取的token0数量
|`amount1Max`| uint256 | 最大获取的token1数量
### addLiquidity
```solidity
  function addLiquidity(
    struct Position.Info self,
    struct Position.AddParams params,
    mapping(address => bytes) sellPath,
    mapping(address => bytes) buyPath
  ) public returns (uint128 liquidity)
```
添加LP到指定头寸


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | 头寸信息
|`params` | struct Position.AddParams | 投资信息
|`sellPath` | mapping(address => bytes) | 卖出代币的路径
|`buyPath` | mapping(address => bytes) | 买入代币的路径

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| struct Position.Info | 添加头寸后获得的LP


### burnAndCollect
```solidity
  function burnAndCollect(
    struct Position.Info pool,
    address proportionX128
  ) public returns (uint256 amount0, uint256 amount1)
```
销毁指定头寸的LP并取回拥有的2种代币


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`pool` | struct Position.Info | Uniswap V3池子信息
|`proportionX128` | address | 要销毁的LP份额

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint256 | 取回的token0数量
|`amount1`| uint256 | 取回的token1数量


### subLiquidity
```solidity
  function subLiquidity(
    struct Position.Info self,
    struct Position.SubParams params
  ) public returns (uint256 amount)
```
减少指定头寸的LP，取回代币并兑换成基金本币。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | 指定的头寸
|`params` | struct Position.SubParams | 池子信息和要减掉的份额

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | 获取的基金本币数量


### assetsOfPool
```solidity
  function assetsOfPool(
    struct Position.Info[] self,
    address pool,
    address token,
    mapping(address => bytes) sellPath,
    address uniV3Factory
  ) public returns (uint256 amount, uint256[])
```
获取某个池子的所有资产（以基金的本币衡量）


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info[] | 指定池子的所有头寸位置
|`pool` | address | 池子地址
|`token` | address | 基金本币地址
|`sellPath` | mapping(address => bytes) | 卖出代币并兑换成基金本币的路径
|`uniV3Factory` | address | Uniswap V3 工厂合约地址

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | 池子的总资产
|`amounts`| uint256[] | 每个头寸的资产


### assets
```solidity
  function assets(
    struct Position.Info self,
    address pool,
    address token,
    mapping(address => bytes) sellPath,
    address uniV3Factory
  ) public returns (uint256 amount)
```
获得一个以基金代币为衡量标准的头寸的资产


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | 指定头寸
|`pool` | address | 头寸所在池子的地址
|`token` | address | 基金本币地址
|`sellPath` | mapping(address => bytes) | 买入代币的路径
|`uniV3Factory` | address | Uniswap V3 工厂合约地址

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | 资产数量


### getAssetsOfSinglePosition
```solidity
  function getAssetsOfSinglePosition(
    struct Position.AssetsOfSinglePosition params
  ) internal returns (uint256 amount0, uint256 amount1)
```
获取一个头寸的资产t0,t1数量，包括未提取的手续费收益


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.AssetsOfSinglePosition | 头寸信息

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint256 | token0 数量
|`amount1`| uint256 | token1 数量


### getFeeGrowthInside
```solidity
  function getFeeGrowthInside(
    struct Position.FeeGrowthInsideParams params
  ) internal returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128)
```
获取已经增长的费用数据


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.FeeGrowthInsideParams | 池子费用累计增长参数

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`feeGrowthInside0X128`| uint256 | 在头寸的刻度边界内，每单位流动性的 token0 的历史费用增长
|`feeGrowthInside1X128`| uint256 | 在头寸的刻度边界内，每单位流动性的 token1 的历史费用增长

