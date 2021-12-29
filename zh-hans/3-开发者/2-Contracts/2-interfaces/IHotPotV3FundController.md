本合约是控制器合约，由基金经理和治理账户通过控制器合约来操作。

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
用指定token销毁HPT。

任何人都可以调用此方法。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 销毁时用于购买 HPT 的代币
|`amount` | uint256 | 代币数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`burned`| address | 销毁掉的HPT数量

