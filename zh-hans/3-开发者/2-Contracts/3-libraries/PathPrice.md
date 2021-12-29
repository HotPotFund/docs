用于计算交易路径的 sqrt 价格的库。


## Functions
### getSqrtPriceX96
```solidity
  function getSqrtPriceX96(
    bytes path
  ) internal returns (uint256 sqrtPriceX96)
```
获取指定路径当前兑换价格的sqrtPriceX96值


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | 兑换路径

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`sqrtPriceX96`| bytes | 给定路径 tokenOut / tokenIn 当前价格的sqrt (X 2^96)值

### getSqrtPriceX96Last
```solidity
  function getSqrtPriceX96Last(
    bytes path
  ) internal returns (uint256 sqrtPriceX96Last)
```
获取指定路径历史兑换价格的sqrtPriceX96Last值


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | 兑换路径

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`sqrtPriceX96Last`| bytes | 给定路径 tokenOut / tokenIn 历史价格的sqrt (X 2^96)值

### verifySlippage
```solidity
  function verifySlippage(
    bytes path,
    address uniV3Factory,
    uint32 maxSqrtSlippage
  ) internal returns (uint256)
```
验证指定的兑换路径交易滑点是否满足设定条件


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | 兑换路径
|`uniV3Factory` | address | Uniswap V3 工厂合约地址
|`maxSqrtSlippage` | uint32 | 最大交易滑点，最大值: 1e4

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`current`| bytes | 路径的当前价格

