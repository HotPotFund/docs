本接口包含可以被治理账号调用的治理方法。

## Functions
### setGovernance
```solidity
  function setGovernance(
    address account
  ) external
```
改变治理账号地址。

这个函数只能被治理账号调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`account` | address | 新的 governance 地址

### setVerifiedToken
```solidity
  function setVerifiedToken(
    address token,
    bool isVerified
  ) external
```
为所有基金设置要信任的代币。

这个函数只能被治理账号调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 目标代币地址
|`isVerified` | bool | 受信任或不受信任

### setHarvestPath
```solidity
  function setHarvestPath(
    address token,
    bytes path
  ) external
```
设置销毁HPT的代币购买路径

这个函数只能被治理账号调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 目标代币
|`path` | bytes | 用`token`购买HPT的路径

### setMaxSqrtSlippage
```solidity
  function setMaxSqrtSlippage(
    uint32 sqrtSlippage
  ) external
```
返回交易时的最大滑点，取值范围为0-1e4，计算公式为：MaxSwapSlippage = (1-(sqrtSlippage/1e4)^2) * 100%,
如果最大滑点设置为0.5%，那么sqrtSlippage应该设置为9974，此时MaxSwapSlippage = (1-(9974/1e4)^2)*100% = 0.5%

这个函数只能被治理账号调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`sqrtSlippage` | uint32 | 开方价格滑点值: 0-1e4

### setMaxPriceImpact
```solidity
  function setMaxPriceImpact(
    uint32 priceImpact
  ) external
```
设置交易时的最大价格影响值

这个函数只能被治理账号调用。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`priceImpact` | uint32 | 价格影响值: 0-1e4


