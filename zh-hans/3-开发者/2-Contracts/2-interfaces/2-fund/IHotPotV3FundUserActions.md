本接口包含可由投资者调用的方法。


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

