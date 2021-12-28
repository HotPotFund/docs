本接口包含可由控制器合约生成的事件


## Events
### ChangeVerifiedToken
```solidity
  event ChangeVerifiedToken(
    address token,
    bool isVerified
  )
```
调用ChangeVerifiedToken设置受信任代币时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`token`| address | 目标代币
|`isVerified`| bool | 是否受信任
### Harvest
```solidity
  event Harvest(
    address token,
    uint256 amount,
    uint256 burned
  )
```
调用Harvest用指定token销毁HPT时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`token`| address | 销毁HPT时，用来购买HPT的本金代币
|`amount`| uint256 | `token`数量
|`burned`| uint256 | 销毁掉的HPT数量
### SetHarvestPath
```solidity
  event SetHarvestPath(
    address token,
    bytes path
  )
```
当调用setHarvestPath设置HPT销毁路径时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`token`| address | 目标代币
|`path`| bytes | HPT购买路径
### SetGovernance
```solidity
  event SetGovernance(
    address account
  )
```
当调用setGovernance设置governance时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`account`| address | 新的 governance 地址
### SetMaxSqrtSlippage
```solidity
  event SetMaxSqrtSlippage(
    uint256 sqrtSlippage
  )
```
当调用 setMaxSqrtSlippage 设置最大交易滑点时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`sqrtSlippage`| uint256 | 开方价格滑点值: 0-1e4
### SetMaxPriceImpact
```solidity
  event SetMaxPriceImpact(
    uint256 priceImpact
  )
```
当调用 setMaxPriceImpact 设置最大价格影响时触发


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`priceImpact`| uint256 | 价格影响值: 0-1e4

