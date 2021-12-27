Fund managers and governance need to operate through controller contract.

```solidity
interface IHotPotV3FundController is IManagerActions, IGovernanceActions, IControllerState, IControllerEvents {
    function harvest(address token, uint amount) external returns(uint burned);
}
```

## Functions
### harvest
```solidity
  function harvest(
    address token,
    uint256 amount
  ) external returns (uint256 burned)
```
All the fund share is used to burn HPT

Anyone can call this function

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Types of tokens used to purchase HPT when burning
|`amount` | uint256 | Amount of tokens

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`burned`| address | Quantity burned

