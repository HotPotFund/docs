Contains methods that can be called by investor.


## Functions
### deposit
```solidity
  function deposit(
    uint256 amount
  ) external returns (uint256 share)
```
The user deposits the local token of the fund

The deposit function is suitable for ERC20 funds, if it is an ETH fund (internally converted to WETH9), it should be directly transferred to the fund contract.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint256 | Deposit amount

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`share`| uint256 | Fund shares obtained by users
### withdraw
```solidity
  function withdraw(
    uint256 share,
    uint256 amountMin,
    uint256 deadline
  ) external returns (uint256 amount)
```
The user withdraws some local token of the specified share


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`share` | uint256 | Amount of fund shares withdrawn
|`amountMin` | uint256 | Minimum extraction value
|`deadline` | uint256 | The deadline timestamp of transaction

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | Returns the amount of fund local token

