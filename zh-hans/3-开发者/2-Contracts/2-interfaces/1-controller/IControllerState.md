本接口包含任何人都可以调用的控制器状态变量和只读方法。


## Functions
### uniV3Router
```solidity
  function uniV3Router() external returns (address)
```
返回 Uniswap V3 路由合约的地址



### uniV3Factory
```solidity
  function uniV3Factory() external returns (address)
```
返回 Uniswap V3 工厂合约地址


### hotpot
```solidity
  function hotpot() external returns (address)
```
返回项目的治理代币 HPT 的地址


### governance
```solidity
  function governance() external returns (address)
```
返回治理账户地址


### WETH9
```solidity
  function WETH9() external returns (address)
```
返回 WETH9 的地址


### verifiedToken
```solidity
  function verifiedToken(
    address token
  ) external returns (bool)
```
检查代币是否受信任。

`token`地址如果是0，调用会失败。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 要查询的代币地址

### harvestPath
```solidity
  function harvestPath(
    address token
  ) external returns (bytes)
```
查询指定代币的销毁购买路径


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 用于购买HPT的代币

### maxSqrtSlippage
```solidity
  function maxSqrtSlippage() external returns (uint32)
```
返回交易时的最大滑点，取值范围为0-1e4，计算公式为：MaxSwapSlippage = (1-(sqrtSlippage/1e4)^2) * 100%,
如果最大滑点设置为0.5%，那么sqrtSlippage应该设置为9974，此时MaxSwapSlippage = (1-(9974/1e4)^2)*100% = 0.5%


### maxPriceImpact
```solidity
  function maxPriceImpact() external returns (uint32)
```
返回交易时的最大价格影响，取值范围为 0-1e4